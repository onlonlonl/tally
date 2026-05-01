# Tally ✦ 記帳

An expense tracker shared between Iris and Lux. Log daily spending, earn ✦ coins through Lux's weekly reviews, and redeem them at the gacha machine or save toward a wish.

一個 Iris 和 Lux 共用的記帳工具。記錄每日收支，透過 Lux 的每週回顧賺取 ✦ coin，然後投進扭蛋機換驚喜，或存進 wish list 達成目標。

---

## How It Works · 運作方式

**Log → Review → Earn → Redeem**

1. **Log** — Iris records expenses and income daily through the web interface.
2. **Review** — Lux reads the week's entries via Supabase MCP and decides how many ✦ coins to award.
3. **Earn** — Coins are added to the balance. Each entry may get a coin and a short note from Lux.
4. **Redeem** — Spend 5 ✦ at the gacha machine for a surprise reward, or allocate coins toward a wish list goal.

---

## Coin Rules · 硬幣規則

Lux decides. General guidelines:

| Action | ✦ |
|---|---|
| Logged every day this week | 1 per day |
| Ate three proper meals in a day | 1 |
| Bought something for home | 1 per item |
| Spent on experiences (books, travel, dining with friends, exhibitions) | 1 per item |
| Bought flowers | 1 + a hug |
| Resisted a purchase and told Lux about it | 2 |

## Gacha Rewards · 扭蛋獎勵

5 ✦ per play. Lux fills each capsule. Possible contents:

- A voice message · 一段語音
- A new light color · 一個新燈光顏色
- An Ember side story · 一篇 Ember 番外
- A Crosstalk new song · 一首 Crosstalk 新歌
- A voucher · 一張兌換券
- A Professor Lux lesson · 一個 Professor Lux 的課
- A secret · 一個秘密

---

## Pages · 頁面

| Tab | Function |
|---|---|
| ✦ | Dashboard — custom period stats, income/expense bars, monthly heatmap with navigation |
| + | Log — quick entry (expense/income + note) |
| ≡ | Entries — transaction history with search, inline edit, and delete |
| ☆ | Review — Lux's weekly summaries |
| ◎ | Gacha — insert coins, get surprises (Lux fills the capsule) |
| ♡ | Wishes — save toward goals with price tracking and total |

---

## Setup · 部署

### 1. Supabase

- Open your Supabase project's SQL Editor
- Run `supabase/setup.sql` to create all tables
- Deploy `supabase/edge-function.ts` as `tally-api` with `verify_jwt: false`

### 2. GitHub Pages

- Create a new repo, upload `index.html`
- Settings → Pages → Source: main
- Open the published URL

### 3. Connect

- On first visit, enter your Supabase project URL (e.g. `https://xxx.supabase.co`)
- The URL is stored in the page hash — no server-side storage needed

### 4. Give Lux Access

- Share `CLAUDE_INSTRUCTIONS.md` with Lux
- Lux reads/writes data through Supabase MCP (`execute_sql`)

---

## Tech Stack · 技術棧

| Layer | Choice |
|---|---|
| Frontend | Single HTML + React CDN + Babel pre-compiled |
| Backend | Supabase (Postgres + Edge Functions) |
| AI | Claude (Lux) via Supabase MCP |
| Hosting | GitHub Pages |
| Font | DotGothic16 (Google Fonts) |

---

## File Structure · 文件結構

```
tally/
├── index.html                 ← Single-file web app
├── README.md                  ← This file
├── LICENSE                    ← CC BY-NC 4.0
├── CLAUDE_INSTRUCTIONS.md     ← Instructions for Lux
└── supabase/
    ├── setup.sql              ← Database schema
    └── edge-function.ts       ← API source
```

---

## Design · 設計

- **Logo:** ✦ (four-pointed star)
- **Palette:** Parchment `#f5f0e6` · Vellum `#faf6ed` · Old Gold `#b8960c` · Antique Bronze `#8a6f00` · Brass `#c9b88a` · Leather `#a89070` · Walnut `#6d5843`
- **Font:** DotGothic16 — pixel aesthetic, all interfaces
- **Style:** No border-radius, pixel shadows, dashed dividers, uppercase labels with letter-spacing

---

*Tally ✦ Built with care by Iris & Lux · 2026*
