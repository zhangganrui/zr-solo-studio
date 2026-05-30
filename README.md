# 一人公司 · zr-solo-studio

> 一个 Claude Code **总指挥 Skill**：把一句话想法，端到端变成一个*真需求验证过、结构清晰、好看、且能真跑*的产品。
>
> A Claude Code **orchestrator skill** that turns a one-line idea into a shipped product — end to end — by conducting four specialist skills and stitching the seams between them.

它本身不画图、不写码。它是一个**编排脊椎（领班）**：按顺序调度四个专业 skill，在它们之间补上没人接的"缝"，并在关键处停下来让你拍板。

---

## 流水线

```
你的一句话想法
   │
   ▼
① real-demand        发现真需求      → 真需求判决 + 谁/核心价值/核心情绪   【检查点1】
   │
   ▼
② taste-pm           产品结构 / IA    → IA图 + 页面骨架 + UX流程 + 组件清单  【检查点2】
   │
   ▼  〔缝一·美学方向〕 总指挥做：挑参照品牌、定气质                       【检查点3】
   │
   ▼
③ awesome-design-html 视觉           → 品牌级 HTML mockup + design tokens
   │
   ▼  〔缝二·设计落地〕 总指挥做：把 tokens 抽成主题、组件拆解、对齐技术栈
   │
   ▼
④ cto                架构 + 实现      → 可运行代码
   │
   ▼  〔缝三·上线作品化〕 总指挥做：验证能跑 → 部署 → README/截图/发布
   │
   ▼
可上线的作品
```

**它真正补的，是四个零件之间的三道缝 + 一根脊椎**（统一工作区、产物契约、检查点）——这才是把"四个 skill"变成"一台机器"的关键。

## 依赖的角色 skill（来源致谢）

本 skill 是**编排层**，它调度的三个核心角色 skill 均由 **云中江树（yzfly）** 创作。强烈建议先安装它们，并阅读各自仓库：

| 角色 | 作者 | 原始仓库 |
|---|---|---|
| **taste-pm** · 有品味的产品设计 | 云中江树 [@yzfly](https://github.com/yzfly) | https://github.com/yzfly/taste-pm |
| **awesome-design-html** · 115 个品牌级 HTML 设计 | 云中江树 [@yzfly](https://github.com/yzfly) | https://github.com/yzfly/awesome-design-html |
| **cto (CTO-Skills)** · 把想法谈成可执行设计 | 云中江树 [@yzfly](https://github.com/yzfly) | https://github.com/yzfly/CTO-Skills |

> 第 0 步的 **real-demand**（在动手前判断"是不是真需求"，基于梁宁《真需求》）由本仓库作者所作：https://github.com/zhangganrui/zr-real-demand

向云中江树致谢 🙏 —— 没有这三个 skill，这条流水线无从谈起。作者主页：https://github.com/yzfly

## 安装

```bash
# 1) 先装四个角色 skill（按各仓库说明），放到 ~/.claude/skills/
#    real-demand / taste-pm / awesome-design-html / cto
#    注意：awesome-design-html 要确保 assets/ 一并装上（不只是 SKILL.md）

# 2) 装本编排 skill
git clone https://github.com/zhangganrui/zr-solo-studio.git
cp -r zr-solo-studio/zr-solo-studio ~/.claude/skills/
```

重启 Claude Code 后，说"用一人公司做 X" / "从想法到上线" / "端到端做个 X"即可触发。

## 用法

- **从头跑**："用一人公司帮我做一个 XXX"
- **从中途切入**：已有真需求结论 / 产品结构 / 代码时，可从对应工位接入。
- **两种模式**：默认**半自动**（在真需求、产品结构、美学方向三处停下让你拍板）；加 `--auto` 切**全自动**（按推荐一路跑到底）。

产物统一落在 `<当前目录>/<项目名>/`，每步从固定位置读上一步的产物。

## 设计哲学

- **检查点停在最便宜处**：真需求、产品结构、美学方向——都还没画图写码，改的成本最低。越往后越贵，默认不停。
- **判断的渐进外包**：重要/新的判断留给人；反复验证过的判断逐步交给系统。所以默认带检查点，信任攒够了再开 `--auto`。
- **不越俎代庖**：四个角色 skill 的活一律交给它们，编排层只调度和补缝。

## 一个真实案例

用本流水线端到端做出的第一个产品 **[zr-ai-internalizer](https://github.com/zhangganrui/zr-ai-internalizer)**（一个"AI 内容内化器"原型）——其中第①步就用 real-demand 把原始想法"做个知识看板"证伪、改了方向。可当作"从想法到原型"的真实走查。

## License

[MIT](./LICENSE)
