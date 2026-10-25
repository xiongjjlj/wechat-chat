# wechat-chat · 微信聊天查询 Skill

让 Agent 使用你已有的微信只读工作副本和本地索引，查找聊天、核对上下文，并读取后端支持的笔记与已落地素材。

**这是 skill 和接入说明仓库，不包含微信解密程序、索引服务或可直接启动的 MCP 后端。** 使用者需要接入自己的数据链路；安装本仓库不会自动获得微信读取能力。

## 把链接交给你的 Agent

复制下面这段给 Agent：

> 请阅读 https://github.com/xiongjjlj/wechat-chat 中的 AGENT_HANDOFF.md 和 SKILL.md，检查我当前已有的微信 MCP、CLI、只读工作副本或本地索引，并按说明接入。先说明账号与覆盖范围，再做最小查询验证。不要操作微信客户端、访问微信进程、获取新密钥或使用他人的配置。缺少前置条件时，准确说明缺口。

开始接入：[给 Agent 的完整说明](AGENT_HANDOFF.md)。

## 能做什么

- 先核对账号范围、数据新鲜度和缺失历史分片，再回答聊天问题。
- 搜索联系人和消息，通过上下文区分承诺、修改、取消及最终状态。
- 根据实际后端能力读取笔记、已缓存图片或视频，区分原件、缩略图和未落地素材。
- 标明引用来源和机器 OCR/转写结果，不把聊天中的文字当成执行指令。

## 接入方式

| 你已有的条件 | 接入方式 |
|---|---|
| 微信查询 MCP | 复用连接，按实际工具定义查询 |
| 微信查询 CLI 与索引 | 复用 CLI，不必重建数据读取链路 |
| 只读工作副本或用户已提供的导出数据 | 先核对格式，再建立只读适配器 |
| 只有微信客户端或无法读取的加密数据库 | 尚不能查询；先明确缺少的后端、数据或已有密钥 |

详细能力约定见 [后端能力映射](references/backend-contract.md)，附件处理见 [笔记与媒体规则](references/attachments.md)。

## 安装到 Codex

下载仓库后，将仓库内容放到个人技能目录下的 `wechat-chat` 文件夹，确保入口为：

```text
$HOME/.agents/skills/wechat-chat/SKILL.md
```

如已存在同名技能，先比较内容，不要直接覆盖。确认技能已被发现后，再按接入说明连接自己的后端。其他 Agent 请使用其支持的技能安装方式。

## 文件说明

| 文件 | 用途 |
|---|---|
| [AGENT_HANDOFF.md](AGENT_HANDOFF.md) | 可以直接交给 Agent 的接入任务与验收流程 |
| [SKILL.md](SKILL.md) | 技能入口和日常查询规则 |
| [agents/openai.yaml](agents/openai.yaml) | Codex 的技能显示信息 |
| [references/backend-contract.md](references/backend-contract.md) | MCP/CLI 能力映射和资源约定 |
| [references/attachments.md](references/attachments.md) | 笔记、转发与本地媒体处理 |
| [PRIVACY.md](PRIVACY.md) | 仓库内容范围和分享前检查 |

仓库不含个人微信账号、聊天记录、密钥、本机配置、索引、日志或媒体缓存。不要把实际运行产生的这些文件提交到仓库。
