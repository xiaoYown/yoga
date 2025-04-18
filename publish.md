## 发布最新 Yoga 流程

> 干活前先阅读 NOTICE.md

### 1. 准备工作

1. 注册您的 pod, 收到邮件后验证即可

```
pod trunk register your.email@example.com 'Your Name'
```

### 2. Fork Yoga 仓库

### 3. 基于 Yoga.podspec 新建一个 podspec 文件

修改项:

- Copyright 添加说明
- 修改 spec.name
- 修改 spec.version, 功能性修改, 则另起初始版本号(当前仅作 cocoapods 发布, 所以仅基于原始版本号添加 dist.number 即可)
- 修改 spec.homepage 指向你们维护的 fork 仓库
- 更新 spec.source 指向你们的 fork 仓库
- 在 spec.summary 中可以添加说明这是一个维护性发布
- 在 spec.authors 中添加组织的名字

### 4. 提交并发布

```sh
# 创建 tag, tag 与 spec.version 一致
git commit -m "chore: bump version to 1.0.0"
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
# 验证
pod spec lint Your.podspec
# 发布
pod trunk push Your.podspec --allow-warnings
```