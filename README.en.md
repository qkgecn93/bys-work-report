<div align="center">

# Work Report Assistant

**Translate what you did into value your manager recognizes**

Daily & weekly reports · Project updates · Performance reviews · Promotion packets · Year-end summaries · Bad-news reporting

English · [简体中文](./README.md)

![Agent Skills Standard](https://img.shields.io/badge/Agent_Skills-Standard-black)
![Multi-Runtime](https://img.shields.io/badge/Runtime-Multi--Runtime-blue)
![License](https://img.shields.io/badge/License-MIT-green)

</div>

> **Note on language.** This skill is built for reporting inside Chinese workplaces. It handles the specific evaluation systems used there — Alibaba's 361, ByteDance's eight-tier reviews, the 德能勤绩廉 five-dimension framework used across state-owned enterprises and public institutions — and it produces Chinese-language output. The skill body is in Chinese by design. This page explains what it does for anyone evaluating it.

---

## How this differs from other "AI weekly report" tools

Every tool in this category performs **addition** — you type three lines, it inflates them to eight hundred words.

This one does the opposite: it **compresses twenty scattered items into three you can actually defend**, attaches a verifiable number to each, and marks what your manager is supposed to do about it.

Because the reason reports get skimmed and forgotten was never that they were too short.

|  | Typical tools | This skill |
|---|---|---|
| Direction | Expand, polish | **Compress, front-load, strip rhetoric** |
| Numbers | Leave `XX%` for you to fill | Asks you to supply it; marks `[待填]` if you can't. **Never fabricates** |
| Persistence | Starts from scratch every time | Optionally accumulates a local evidence log; daily notes feed year-end reviews |
| Bad news | Not handled | Dedicated module: timing, attribution limits, forwardable version |
| After delivery | Done | Predicts how your manager may respond, and how you'd answer each |

---

## Core capabilities

### 📉 Subtraction, not addition

Give it twenty items, it delivers three to five — and tells you why it cut the rest. Nothing is lost; cuts go to your evidence log.

### 🔢 Verifiable-anchor enforcement

It scans every claim of achievement and requires adjectives be replaced with numbers.

```
❌ Significantly improved response time
✅ API response dropped from 800ms to 200ms

❌ Substantially optimized the workflow
✅ Approval steps cut from 7 to 3; average turnaround from 2 days to 4 hours
```

### 🎯 Action tagging

Every line is tagged with what your manager needs to do — **FYI / Decide / Support / No action**.

If a whole report is nothing but FYI, it tells you: that means you moved nothing this week that required your manager's involvement.

### 📁 Long-term evidence accumulation

Each delivery can append to a local work log. What it stores is not a copy of the finished report — it's the **raw facts before compression**, including the small items that never made it in.

> "Helped the team next door sort out their data definitions" seems trivial today. Next year it may be the only evidence you have under "cross-functional influence."

### ⚠️ Bad-news reporting

Other tools only help you report good news. But the hardest report to write is always the one about a slipped deadline, a missed target, or something you broke.

- **Timing before wording** — the worst mistake with bad news isn't phrasing it badly, it's reporting it late
- **Mandatory three parts** — what happened / who's affected / your options (at least two)
- **Attribution limits** — no naming and blaming, and no excessive self-criticism either
- **A forwardable version** — your manager has to explain this upward too; prepare that layer for them

### 🎭 Simulated review

Have the AI play your direct manager or a promotion committee member, score the draft against fixed criteria, and iterate — capped at two rounds, so it doesn't sand away your own voice.

The reviewer persona is specific: engineering or business background, focused on metrics or on risk. An abstract "manager" produces useless feedback.

### 🏛 Adapts to your evaluation system

Review materials are organized in the vocabulary of your actual environment, not one template for everyone:

- **Tech companies** — impact stories, quantified outcomes, scope levels, peer perspective
- **State-owned enterprises / public institutions** — the 德能勤绩廉 five-section structure, weighted toward conduct and results
- **Unsure** — a general structure, without interrogating you

---

## Three things it will not do

These are hard limits, never crossed:

1. **Never fabricates numbers, dates, or names.** What you didn't provide becomes `[待填]` (to fill in) — it will not invent a plausible-looking figure
2. **Never softens bad news.** "Slight delay" to describe a one-month slip is forbidden
3. **Never pads for you.** If you genuinely did little this week, it won't invent work. It digs for output you didn't recognize as output; failing that, it writes the honest short version

> Reports get verified. A fabricated number caught once costs you more than one bad weekly report.

---

## Install

### One command (auto-detects runtime)

```bash
npx skills-cli install bys-work-report
```

### Manual

Clone this repository and place the entire `bys-work-report/` directory into your tool's skills folder:

| Runtime | Path |
|---|---|
| Claude Code | `~/.claude/skills/` |
| Cowork | Settings → Skills → Import |
| Codex | `~/.codex/skills/` |
| Cursor | `.cursor/skills/` |
| Other compatible runtimes | Follow that tool's skills directory convention |

### As reference material

Installation is optional — pasting `SKILL.md` and the `references/` contents into any AI assistant works just as well.

---

## Usage

Once installed, speak plainly:

```
帮我写个周报              Write my weekly report
```
```
年底要述职了，帮我准备材料   Help me prepare my performance review
```
```
项目要延期了，怎么跟领导说   The project is slipping — how do I tell my manager
```

For the full guided setup (personal profile + evidence log):

```
初始化 不一书工作汇报助手
```

**Setup is not required.** On first use it gets straight to work and only asks about the log after delivering — value first, commitment second.

---

## Where your data lives

Entirely local.

- `工作留档.md` — your evidence log
- `我的汇报档案.md` — your industry, manager's style, evaluation system

Both sit in a folder you choose. Viewable, editable, backup-able, deletable at any time. **Nothing is uploaded or transmitted.**

No web lookups are performed on internal company information. Any web search asks your permission first and states exactly what it intends to look up.

---

## Structure

```
bys-work-report/
├── SKILL.md                        Core: hard limits, checkpoints, mode routing, failure branches
├── references/
│   ├── 00-初始化与欢迎语.md         Onboarding
│   ├── 01-采集与留档.md             Material gathering, evidence log, time boundaries
│   ├── 02-写作规范.md               Subtraction, front-loading, anchors, de-AI-ing
│   ├── 03-述职与考核体系.md         Review structures per evaluation system
│   ├── 04-坏消息汇报.md             Delays, missed targets, incidents
│   ├── 05-模拟评审与预测追问.md      Simulated review and anticipated questions
│   └── 06-交付形式与PPT.md          Delivery formats, template filling, slide rules
└── assets/
    ├── 工作留档-模板.md
    └── 我的汇报档案-模板.md
```

---

## FAQ

**Our company has a fixed weekly report template. Will this work?**
Yes. Send it the blank template or the one you filled in last time, and it maps to your field structure. For Excel files with complex merged cells it will say plainly that it can't fill them — better to say so than to fill them wrong.

**Does it imitate my writing voice?**
It learns your company's internal jargon, formatting conventions, and expected level of detail — but **not your writing quality**. Your past reports may well have been weak; copying them would import the weaknesses.

**Why won't it just fill in the numbers?**
Because reports get verified. It would rather send you off for a one-minute lookup than hand you a figure that leaves you stranded when someone asks where it came from.

**Does it build review slide decks?**
Yes, with a per-slide speaking script — a review is delivered out loud, and the deck is only a prompt. Slide count and script length are derived backward from your allotted time.

---

## About the author

Buyishu (不一书) is an AI adoption consultant and AI creator on Douyin, based in Shijiazhuang, China, helping companies and institutions with AI training, hands-on AI adoption and custom AI workflows. All `bys-` skills: [imbuyishu.com/skills](https://imbuyishu.com/skills/).

## License

MIT
