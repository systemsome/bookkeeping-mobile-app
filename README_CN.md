# 资产记账管家 Android 独立 App（第一版）

## 这是一个独立项目

本项目与原 `systemsome/bookkeeping` 仓库完全分开。它不修改原项目，也不需要把任何文件放进原仓库。

## 当前版本做什么

- Android 原生壳应用，使用系统 WebView 打开 `https://jz.faith.de5.net`。
- 支持网页 JavaScript、浏览器本地存储和 Cookie。
- 网站内导航留在 App 内；其他 HTTPS 网站交给系统浏览器打开。
- 通过 GitHub Actions 在云端构建 APK，无需在自己的 NAS 上安装 Android Studio。

## 重要说明

这是第一版“网站封装 App”，不是重新开发的原生记账系统。登录、账目保存、同步等功能仍由现有网站和服务端负责。若网站自身存在数据持久化或账号隔离问题，封装后仍可能存在，需要单独修复。

## 如何获得 APK（无需本地构建）

1. 在 GitHub 新建一个**全新的仓库**，例如 `bookkeeping-mobile-app`。不要选择或覆盖原有仓库。
2. 将本项目 ZIP 解压，把其中所有文件上传到新仓库根目录。确保 `.github/workflows/build-apk.yml` 也被上传。
3. 打开新仓库的 **Actions** 页面，选择 **Build Android APK**，点击 **Run workflow**。首次也可以直接把文件提交到 `main` 分支触发构建。
4. 等待任务显示绿色成功。
5. 打开该次运行页面底部的 **Artifacts**，下载 `bookkeeping-android-debug-apk`，解压得到 `app-debug.apk`。
6. 把 APK 传到 Android 手机并安装。手机可能会提示允许从该来源安装应用。

## iPhone

此 ZIP 只包含 Android 工程。iOS 版本需要另行准备 Xcode 工程，并使用 macOS/Xcode 构建和签名；Linux GitHub runner 不能直接完成正式 iOS App 构建。

## 安全与限制

- 此工程没有把网站登录密码或任何个人数据写进代码。
- APK 仅访问 HTTPS 网站。
- 这版未包含离线账本数据库、原生推送或生物识别功能。
- 发布正式商店版本前，应进一步测试网站登录、Cookie、文件上传下载、支付/外部链接行为和隐私合规。
