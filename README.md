# Z.ai2api
将 Z.ai 代理为 OpenAI Compatible 格式，支持免令牌、智能处理思考链、图片上传（登录后）等功能  
基于 https://github.com/kbykb/OpenAI-Compatible-API-Proxy-for-Z 使用 AI 辅助重构。

## 功能
- 支持根据官网 /api/models 生成模型列表，并自动选择合适的模型名称。
- （登录后）支持上传图片，使用 GLM 识图系列模型。
- 支持智能识别思考链，完美转换多种格式。

## 要求
Python 3.12+

## 环境
使用 `.env` 文件进行配置。
### `BASE`
  - 上游 API 基础域名
  - 默认值：`https://chat.z.ai`
### `PORT`
  - 服务端口
  - 默认值：`8080`
### `MODEL`
  - 备选模型，在未传入模型时调用
  - 默认值：`GLM-4.5`
### `TOKEN`
  - 访问令牌
  - 如果启用了 `ANONYMOUS_MODE` 可不填
### `ANONYMOUS_MODE`
  - 访客模式，启用后将获取随机令牌
  - 访客模式下不支持上传文件调用视觉模型
  - 默认值：`true`
### `THINK_TAGS_MODE`
  - 思考链格式化模式
  - 可选 `reasoning` `think` `strip` `details`，效果如下
    - "reasoning"
      - reasoning_content: `嗯，用户……`
      - content: `你好！`
    - "think"
      - content: `<think>\n\n嗯，用户……\n\n</think>\n\n你好！`
    - "strip"
      - content: `> 嗯，用户……\n\n你好！`
    - "details"
      - content: `<details type="reasoning" open><div>\n\n嗯，用户……\n\n</div><summary>Thought for 1 seconds</summary></details>\n\n你好！`
### `DEBUG_MODE`
  - 显示调试信息，启用后将显示一些调试信息
  - 默认值：`false`

## 使用
```
git clone https://github.com/hmjz100/Z.ai2api.git
cd Z.ai2api
pip install -r requirements.txt
python app.py
```
