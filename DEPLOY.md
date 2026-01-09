# GitHub Pages 部署指南

## 🚀 方法一：网页端上传（最简单）

### 1. 创建 GitHub 仓库
- 访问 https://github.com 并登录
- 点击右上角 `+` → `New repository`
- 仓库名称：`resignation-calculator`
- 选择 `Public`（必须是公开仓库）
- 不要勾选 "Add a README file"
- 点击 `Create repository`

### 2. 上传文件
- 在新建的仓库页面，点击 `uploading an existing file`
- 将项目文件拖拽上传（或点击选择文件）
- 需要上传的文件：
  - `index.html`
  - `README.md`
  - （可选）`LICENSE` 文件
- 底部提交信息：`Initial commit`
- 点击 `Commit changes`

### 3. 启用 GitHub Pages
- 进入仓库 → 点击 `Settings`
- 左侧菜单找到 `Pages`
- Source 设置：
  - Branch: `main` (或 `master`)
  - Folder: `/ (root)`
- 点击 `Save`
- 等待 2-5 分钟，刷新页面即可看到网站地址

### 4. 访问网站
地址格式：`https://你的用户名.github.io/resignation-calculator/`

---

## 💻 方法二：Git 命令行（推荐）

### 1. 安装 Git
- Windows: https://git-scm.com/download/win
- Mac: `brew install git`
- Linux: `sudo apt install git`

### 2. 配置 Git
```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

### 3. 创建 GitHub 仓库
- 在 GitHub 网站创建空仓库（同方法一第1步）
- 不要初始化 README

### 4. 提交代码
```bash
# 进入项目目录
cd /Users/yikepierdediannao/Documents/王富贵/Resignation_App

# 初始化 Git 仓库
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit: 离职指数计算器"

# 重命名主分支为 main（如果需要）
git branch -M main

# 关联远程仓库
git remote add origin https://github.com/你的用户名/resignation-calculator.git

# 推送代码
git push -u origin main
```

### 5. 启用 GitHub Pages
同方法一第3步

---

## 🔧 方法三：使用 GitHub CLI（gh）

### 1. 安装 GitHub CLI
- Mac: `brew install gh`
- Windows: https://cli.github.com/

### 2. 登录
```bash
gh auth login
```

### 3. 一键部署
```bash
cd /Users/yikepierdediannao/Documents/王富贵/Resignation_App
gh repo create resignation-calculator --public --source=. --remote=origin --push
```

### 4. 启用 GitHub Pages
```bash
gh api \
  --method PUT \
  -H "Accept: application/vnd.github.v3+json" \
  /repos/你的用户名/resignation-calculator/pages \
  -f source='{"branch":"main","path":"/"}'
```

---

## ✅ 部署后检查

### 访问你的网站
```
https://你的用户名.github.io/resignation-calculator/
```

### 常见问题

**Q: 显示 404 错误？**
- 确保仓库名称正确
- 等待 5-10 分钟让 GitHub 部署完成
- 检查文件名是否是 `index.html`（必须是这个名字）

**Q: 页面样式错乱？**
- 确保 Tailwind CSS CDN 链接正确
- 检查浏览器控制台是否有错误

**Q: 如何更新网站？**
```bash
git add .
git commit -m "更新描述"
git push
```
GitHub Pages 会自动重新部署（约 1-2 分钟）

---

## 🎨 自定义域名（可选）

### 1. 准备域名
- 购买域名（如阿里云、腾讯云、GoDaddy）
- 或使用免费域名（如 Freenom）

### 2. 添加 DNS 记录
```
类型: CNAME
主机记录: @
记录值: 你的用户名.github.io
TTL: 600
```

### 3. 在 GitHub 设置
- 仓库 Settings → Pages
- Custom domain 输入你的域名
- 等待 DNS 检查通过
- 勾选 "Enforce HTTPS"

### 4. 创建 CNAME 文件
在项目根目录创建 `CNAME` 文件（无扩展名），内容：
```
yourdomain.com
```

---

## 📊 查看部署状态

### GitHub Pages 部署状态
- 仓库 → Actions 标签页
- 查看部署日志

### 查看访问统计
- 使用 Google Analytics
- 或 GitHub 自带的 Insights（有限）

---

## 🔐 仓库可见性

**重要：GitHub Pages 只支持公开仓库**

如果是私有仓库，需要：
- 升级到 GitHub Team（付费）
- 或使用其他免费托管服务：
  - Vercel
  - Netlify
  - Cloudflare Pages

---

## 🚀 其他免费托管平台

### Vercel（推荐，国内访问快）
```bash
npm install -g vercel
vercel
```

### Netlify
- 拖拽上传即可
- 自动 HTTPS

### Cloudflare Pages
- 全球 CDN 加速
- 无限带宽

---

## 📱 分享链接

部署成功后，将以下内容分享到小红书/朋友圈：

```
💊 今日离职指数计算器

测测你的打工精神状态！
🔗 https://你的用户名.github.io/resignation-calculator/

#打工人 #离职 #职场 #测试
```

---

**祝部署顺利！有任何问题随时问 🎉**
