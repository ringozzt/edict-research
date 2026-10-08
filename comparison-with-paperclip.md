# Edict × Paperclip：同一赛道的两种解法

> 跨项目合成文档。两份独立调研：[edict-research](./README.md)（2026-10-08）· [paperclip-research](https://github.com/ringozzt/paperclip-research)（2026-10-02）
> 一句话：**Paperclip 像 HR+财务+审计（管人），Edict 像 ISO 流程体系（管事）。**

## 硬数据对照（实测）

| | Edict | Paperclip |
|---|---|---|
| 仓库 | cft0808/edict | paperclipai/paperclip |
| star / fork | 16,977 / 1,766（10-08） | 95,678 / 16,231（10-02） |
| 创建 | 2026-02-23 | 2026-03-02 |
| 授权 | MIT | MIT |
| 技术栈 | Python（后端仅标准库）+ React 18 看板 | TypeScript 全栈（Node.js server + React UI） |
| 运行底座 | OpenClaw（调度外包） | 自研 control plane（自托管，端口 3100） |

## 相同点：同一个赛道

1. **问题意识一致**：单个 Agent 不可靠（幻觉、失忆、烧钱），要靠"系统"而非"更聪明的模型"来兜底。
2. **都是 control plane**：不教你怎么造 agent，管 agent 组成的"组织"如何运转。
3. **可观测 + 可审计是共识**：Edict 的军机处看板/奏折归档 ≈ Paperclip 的 Activity & Events/审批门。
4. **都用组织隐喻**：Edict 用朝廷三省六部，Paperclip 用公司 org chart——隐喻不同，意图相同：给 agent 之间的关系一个人类可理解的形状。

## 不同点：管人 vs 管事

| 维度 | Edict（管事） | Paperclip（管人） |
|---|---|---|
| 回答的问题 | 如何让一群 agent **把一件事办靠谱** | 如何**管理一群 agent 员工** |
| 核心机制 | 门下省封驳（方案审核前置）+ allowAgents 权限白名单 | heartbeat（能收心跳就是员工）+ org chart + 预算硬停 |
| 质量观 | **审核前置**：方案不合格直接打回，不许执行 | **治理后置**：审批门 + 目标 ancestry + 可回滚 |
| 干预方式 | 看板上叫停/取消/恢复单个任务 | 三级预算到线自动暂停、配置变更版本化 |
| 组织模型 | 固定朝廷：太子→三省→六部，指挥链写死 | 可调公司：12 种角色混编，Self-Organization 可提议调架构 |
| Agent 规模假设 | 一次办好一件事（任务流转） | 20 个 agent 常驻（"只有一个 agent 你不需要 Paperclip"） |
| 技术路线 | 调度外包 OpenClaw，自研制度层+看板 | 全栈自研，连 runtime/沙盒/记忆都做成插件 |
| 野心 | 把任务流转做扎实 | Agentic OS：MAXIMIZER MODE、组织自动学习 |

## 最值得玩味的三组对照

1. **"谁来审"**：Edict 设了一个专职审核部门（门下省），审核是**编制**；Paperclip 用审批门 + 目标 ancestry，审核是**流程**。编制 vs 流程，东方官僚制 vs 西方公司制——隐喻和解法是自洽的。
2. **"不可靠怎么办"**：Edict 的答案是**分权制衡**（六部不可横向串联，互相监督）；Paperclip 的答案是**心跳 + 预算**（还活着就继续干，烧超了就停）。一个防"作恶/犯错"，一个防"失联/烧钱"。
3. **"轻 vs 重"**：Edict 后端仅 Python 标准库，一天能跑起来；Paperclip 自带嵌入式 PostgreSQL、十二系统、插件生态，是"重"的 control plane。Edict 是**战术工具**，Paperclip 是**战略平台**。

## 能拼在一起吗

能，而且互补：Paperclip 管"雇谁、花多少、目标是什么"，Edict 管"这件事怎么办靠谱"。一个组织的完整 control plane 需要两层——**Paperclip 是公司，Edict 是 ISO 体系**。短期看 Edict 更容易落地（轻、聚焦）；长期看 Paperclip 的天花板更高（组织级基础设施）。

## 给 k2 的启示

- **战术级抄 Edict**：审核前置（门下省式质量关卡）+ 权限白名单（allowAgents 指挥链写死）——两周能落地。
- **战略级抄 Paperclip**：目标 ancestry（agent 看到的不只是任务标题，还有"为什么做"）+ 预算硬停（runaway loop 是最痛的坑）——这是 control plane 的长期形态。
- **别抄隐喻，抄机制**：朝廷和公司的皮都可以扒，留下的是"审核前置、权限写死、预算硬停"三件事。

---
*Edict 调研：[ringozzt/edict-research](https://github.com/ringozzt/edict-research) · Paperclip 调研：[ringozzt/paperclip-research](https://github.com/ringozzt/paperclip-research)*
