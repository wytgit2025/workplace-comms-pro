# Workplace Comms Pro

> **写周报、给老板汇报、找别的部门帮忙——这些事最烦的不是写，是"想不起来这周到底干了啥"。**

一个跨 **飞书 / 钉钉 / 企业微信** 的中文职场内部沟通写作 Skill。自动拉取你在各办公平台上的工作痕迹，按中文职场分寸感，写成老板 30 秒能看完的内部沟通稿。

这是 Anthropic 官方 [`internal-comms`](https://github.com/anthropics/skills) 的中文增强版。

## 解决什么痛点

- 周五下午想写周报，盯着空白文档想不起来这周干了什么
- 给老板汇报，写了三段铺垫他还不知道你要批多少钱
- 找法务帮忙，甩一句"在吗"，对方还得追问你什么事、什么时候要
- 每个平台一个待办，周报要来回切三个 app 抄数据

## 支持六种文体

| 文体 | 什么时候用 | 亮点 |
|---|---|---|
| 📋 周报 | "写周报""周五交周报" | 含极简三行版，发群里/站会直接用 |
| 📊 向上汇报 | "给老板汇报""月度汇报" | 结论先行、带方案抛问题 |
| 🚀 项目启动通知 | "kick-off""发个启动通知" | 背景/目标/范围/分工/时间点 |
| 🤝 跨部门求助 | "找XX部门帮忙" | 给足上下文、降低对方协作成本 |
| 📢 全员通讯 | "部门月报""公司newsletter" | 分板块、按重要性排、不是流水账 |
| ❓ 全员FAQ | "整理常见问题""新人问答" | 高频问题标准答案、减少重复沟通 |

## 和现有方案的区别

| 方案 | 问题 |
|---|---|
| Anthropic 官方 `internal-comms` | 英文、静态模板、不接中国办公平台 |
| 豆包 `lark-workflow-standup-report` | 只做飞书单平台、只做每日站会、不做写作 |
| 自己写 prompt | 每次重新想结构、没有中文职场分寸感、不自动拉数据 |

**本技能补的空：跨三平台 + 中文职场分寸感 + 自动拉数成稿。**

## 三平台数据接入

| 平台 | 接入方式 | 状态 |
|---|---|---|
| 飞书 | `lark-cli task +get-my-tasks` / `lark-cli calendar +agenda` | ✅ 已验证通道可用 |
| 钉钉 | 钉钉待办 MCP / DWS CLI | 🟡 配好 MCP 即用 |
| 企业微信 | 企微 OpenClaw 插件 To-Do MCP | 🟡 配好 MCP 即用 |

没配 MCP 也能用——自动降级为你口述要点、Skill 负责组织成文。

## 安装

### 豆包工作

把 `workplace-comms-pro/` 整个目录放到你的技能目录（如 `.user_skills/`），然后在对话里说"帮我写个周报"即可触发。

### 其他兼容 Agent 环境

本 Skill 遵循开放的 Agent Skills 格式（YAML frontmatter + Markdown），任何支持该格式的 Agent 环境都可加载。

## 项目结构

```
workplace-comms-pro/
├── SKILL.md                          # 主流程：识别文体→拉数据→加载指南→成稿→按平台输出
└── references/
    ├── weekly-report.md              # 周报（含极简三行版）
    ├── upward-update.md              # 向上汇报
    ├── project-kickoff.md           # 项目启动通知
    ├── cross-team-request.md         # 跨部门求助
    ├── company-newsletter.md         # 全员通讯/部门月报
    └── faq-answers.md                # 全员FAQ
```

## License

MIT