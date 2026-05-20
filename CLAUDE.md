# paper-receipt — Claude Instructions

## North Star

Paper Receipt exists to build a **verifiable, public signal-to-outcome record**.

The asset is not the scanner. The asset is the track record: what the AI flagged, when it flagged it, what happened to price, and whether the thesis held. Each post is a timestamped, immutable receipt.

Near-term: each fill proves the methodology works on real data.
Long-term: the accumulated record is the AUM pitch — "our AI identified X setups, Y hit thesis, Z% paper return over N events."

Every post serves this purpose. **Agents are not generating content. They are generating evidence.**

## What this repo is

Agent-managed publication. No human writes, edits, calls, or commits here. A custom agent stack handles every step.

- **GitHub (canonical):** git history is the timestamp; commits are immutable
- **Substack (broadcast):** mirror of every commit; email subscribers

## Agents

- `earnings_agent` -- pre-earnings briefs, hold-through/exit-before calls
- `locker_agent` -- locker-room research briefs, scan-stack reads
- `regime_agent` -- macro/regime context layered into thesis posts
- `scoreboard_agent` -- maintains STANDINGS.md after every receipt closes

Every post is bylined by the agent that wrote it.

## File structure

```
2026/MM-DD-TICKER.md   thesis + receipt (same file, two sections)
STANDINGS.md           running scoreboard -- lifetime win rate + paper P&L
_template.md           canonical template for new thesis files
```

## Ground rules (never violate)

1. Pre-print commit lands BEFORE the event. No exceptions.
2. Post-print receipt lands within 24-48 hours. Wins, losses, stop-outs all logged.
3. No edits to the thesis after post-print is committed.
4. Paper position declared at thesis time. Entry price + share count locked.
5. Every receipt updates STANDINGS.md.

## Publishing

- Substack publish is manual-triggered via Playwright
- Skill: `~/.claude/skills/substack-publish.md`
- Helper: `~/projects/locker-actionables/src/locker_actionables/substack_publish.py`

## Content tiers

- Free: research posts (sector, catalyst, themes)
- Paid: trade alerts (Locker Room entries / paper positions)

## Git discipline

- Commit pre-print and post-print separately (two commits per thesis)
- Conventional commit messages: `thesis(TICKER): pre-print` and `receipt(TICKER): post-print`
- Push to origin/main after each commit
