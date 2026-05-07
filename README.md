# Yuanbao Patched — 元宝群聊媒体修复插件

> 修复官方 yuanbao 适配器的群聊媒体丢失 bug：非 @Bot 消息中的图片/文件现在能正确保留并在后续 @Bot 时恢复。

## 问题

官方适配器在群聊中，非 @Bot 的消息只把占位符文本（如 `[image]`）存入会话 transcript，导致后续 AI 被 @Bot 触发时无法恢复图片/文件资源。

## 方案

观察阶段只记录轻量锚点 `[image|ybres:resourceId]`，@Bot 触发时再从最近 50 条历史中扫描锚点、下载并缓存到本地，每轮最多处理 7 个媒体文件。

## 安装

```bash
hermes plugins install https://github.com/ptbsare/yuanbao-patched-hermes-plugin/
```

## 配置

```bash
export YUANBAO_PATCHED_APP_ID="your-app-id"
export YUANBAO_PATCHED_APP_SECRET="your-app-secret"
```

可选：`YUANBAO_PATCHED_BOT_ID`、`YUANBAO_PATCHED_WS_URL`、`YUANBAO_PATCHED_API_DOMAIN`

## 依赖

`websockets`、`httpx`（hermes plugins install 会自动安装）

## 作者

ptbsare
