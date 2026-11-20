# Scout Help Center

Mintlify-powered docs site that becomes `help.trychora.com`.

## Structure

```
scout-docs/
├── docs.json              # Mintlify config (nav, colors, logo, domain)
├── introduction.mdx       # Landing page
├── hirers/                # Articles for hiring teams
│   ├── create-programme.mdx
│   ├── add-roles.mdx
│   ├── invite-scouts.mdx
│   ├── set-scout-fees.mdx
│   └── payouts.mdx
├── scouts/                # Articles for scouts
│   ├── join-programme.mdx
│   ├── share-role-links.mdx
│   ├── track-referrals.mdx
│   ├── setup-stripe.mdx
│   └── email-notifications.mdx
├── logo/                  # Rendered in the top-left of every page
│   ├── light.svg
│   └── dark.svg
└── favicon.svg
```

## Local preview

Install the Mintlify CLI once:

```bash
npm i -g mintlify
```

Then from inside `scout-docs/`:

```bash
mintlify dev
```

Serves on http://localhost:3000 with hot reload on every MDX save.

## Deploy

1. Push `scout-docs/` to its own GitHub repo (e.g. `trychora/scout-docs`), or keep it in this monorepo and set the Mintlify project's **root** to `scout-docs`.
2. Sign up at [mintlify.com](https://mintlify.com) with the GitHub account that owns the repo.
3. Install the Mintlify GitHub App on that repo.
4. In the Mintlify dashboard: **Settings → Custom domain** → add `help.trychora.com`.
5. Add the CNAME Mintlify prints to your DNS provider (points to `cname.mintlify.com`).
6. Mintlify auto-deploys on every push to `main` (or whichever branch you pick).

## Writing new articles

1. Add an MDX file in the right folder (hirers/ or scouts/).
2. Add the frontmatter:
   ```yaml
   ---
   title: Human-readable title
   description: One-sentence summary (shown in search + social cards)
   ---
   ```
3. Add its path (without `.mdx`) to the relevant `pages` array in `docs.json`.
4. Write using Markdown + Mintlify components: `<Tip>`, `<Note>`, `<Warning>`, `<Card>`, `<CardGroup>`, `<Tabs>`, `<Accordion>`, `<Steps>`. Full list: https://mintlify.com/docs/content/components

## Conventions

- **Voice**: direct, second-person, no filler. "Click X, then do Y."
- **Links**: internal cross-links use `/path/to/article` (no file extension). External links hit `trychora.com/...` directly.
- **Code**: fenced blocks with a language hint for syntax highlighting.
- **Tables**: use for comparing concepts side-by-side (pricing tiers, scout classes, etc.).
- **Images**: live under `/images/` once we have any. Reference as `/images/<name>.png`.
