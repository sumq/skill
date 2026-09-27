# 成长型项目方法论 Skills

这是一组面向真实项目开发的 Codex Skills，用来提升两种可以跨领域迁移的能力：

1. 从模糊目标中找出关键需求、约束和未知，形成可验证的实施路线。
2. 面对复杂卡点时，用事实、假设和最小实验定位原因，完成修复与防回归验证。

它们适用于自动化程序、网站、数据流程、视频制作等项目。Skill 提供统一的判断方法；具体设计、编程、视频或其他专业工作仍应结合对应领域的工具与规范。

## 包含的 Skills

| Skill | 适用场景 | 核心能力 |
| --- | --- | --- |
| [`plan-with-evidence`](plan-with-evidence/SKILL.md) | 新项目、重要功能、约束变化后的重新规划 | 主动澄清关键需求，拆解能力和依赖，识别最大未知，设计最小实验和阶段门禁 |
| [`solve-with-evidence`](solve-with-evidence/SKILL.md) | 预期与实际不一致、反复失败或难以定位的技术和制作卡点 | 固定现象，定位故障边界，提出可证伪假设，设计区分实验，验证解决方案 |

## 设计原则

这两个 Skill 的目标是随着项目经验增加而变得更准确，而不是变成越来越长的案例合集。

每个 Skill 分为四层：

```text
SKILL.md                 稳定、精简的核心工作方法
references/patterns.md   有触发条件和适用边界的问题模式
references/evolution.md  经验筛选、晋升、合并和淘汰规则
references/evaluation.md 跨领域验收案例和评价标准
```

新项目中的经验不会直接写进核心方法。它会先成为候选经验，再判断应该：

- 支持已有规则；
- 收窄规则的适用范围；
- 合并重复规则；
- 降级为领域知识；
- 删除已失效规则；
- 在证据充分时形成新模式。

Skill 的成长以决策质量衡量，例如是否更早发现关键缺口、减少无效质询、降低返工和避免错误归因，不以文件长度或规则数量衡量。

## 主动质询规则

Skill 会主动询问那些不同答案会改变目标、完成标准、技术路线、重要成本或权限的问题。

它不会重复询问用户已经回答的内容，也不会把可以从代码、日志、文档和现场状态中自行查明的问题交给用户。明确、低风险的小任务会直接执行并做比例适当的验证。

## 安装

### 方式一：让 Codex 安装

可以在 Codex 中使用 `skill-installer`，分别安装这两个 GitHub 路径：

```text
https://github.com/sumq/skill/tree/main/plan-with-evidence
https://github.com/sumq/skill/tree/main/solve-with-evidence
```

### 方式二：手动安装

克隆仓库：

```powershell
git clone https://github.com/sumq/skill.git
```

把所需目录复制到个人 Codex Skills 目录：

```powershell
Copy-Item -Recurse .\skill\plan-with-evidence "$env:USERPROFILE\.codex\skills\plan-with-evidence"
Copy-Item -Recurse .\skill\solve-with-evidence "$env:USERPROFILE\.codex\skills\solve-with-evidence"
```

如果目标目录已经存在，请先审阅差异，再决定如何更新，避免覆盖自己的修改。重新打开 Codex 会话后即可在可用 Skills 中发现它们。

## 使用示例

规划一个新项目：

```text
使用 $plan-with-evidence 分析这个新项目。主动质询会改变路线的关键缺口，找出最需要先验证的未知，并制定分阶段方案。
```

分析一个复杂卡点：

```text
使用 $solve-with-evidence 分析这个故障。先调查代码、日志和现有产物，再定位最后正确点与第一错误点，用证据区分假设并验证解决方案。
```

项目结束后提炼经验：

```text
复盘这个项目的关键转折，按照成长规则生成候选经验。优先合并已有模式；证据不足时保留为候选，不要求新增规则。
```

如果希望真正更新全局 Skill，请明确提出更新请求。普通项目复盘只生成候选经验，不会持续在后台自动改写 Skill。

## 两个 Skill 的分工

```text
目标、范围或完成标准不清楚
        ↓
plan-with-evidence
        ↓
形成可验证的实施路线
        ↓
执行过程中出现具体异常
        ↓
solve-with-evidence
        ↓
局部问题：修复并继续
核心假设被推翻：带着证据返回重新规划
```

`plan-with-evidence` 回答“要实现什么、先验证什么、怎样才算完成”。

`solve-with-evidence` 回答“哪一步开始出错、哪些原因可以被实验区分、怎样证明解决有效”。

## 当前成熟度

当前版本为 `0.1.0` 试用版。Skill 的结构、元数据和引用关系已经过校验，并包含自动化、网站、视频和简单任务的设计时验收场景。

这些案例用于防止明显误用，不等于已经证明跨领域效率提升。后续版本需要用新的真实项目比较质询价值、实验选择、返工成本和问题解决质量，再决定规则的保留、修改或淘汰。

## 仓库结构

```text
.
├─ README.md
├─ plan-with-evidence/
│  ├─ SKILL.md
│  ├─ agents/openai.yaml
│  └─ references/
│     ├─ patterns.md
│     ├─ evolution.md
│     └─ evaluation.md
└─ solve-with-evidence/
   ├─ SKILL.md
   ├─ agents/openai.yaml
   └─ references/
      ├─ patterns.md
      ├─ evolution.md
      └─ evaluation.md
```
