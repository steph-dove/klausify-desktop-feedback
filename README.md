# Klaussy — Landing Page & Feedback

This repo hosts two things:

1. The landing page for [Klaussy](https://github.com/steph-dove/klausify-desktop) (served via GitHub Pages).
2. The public issue tracker for bug reports and feature requests.

## Report a bug / request a feature

Open an issue in the [Issues tab](https://github.com/steph-dove/klausify-desktop-feedback/issues). Include:
- macOS version
- Klaussy version (About → Version)
- Steps to reproduce
- What you expected vs. what happened
- Logs from `~/Library/Logs/Klaussy/main.log` if relevant

## Development

Plain HTML + CSS — no build step.

```bash
# Preview locally
python3 -m http.server 8080
# Then open http://localhost:8080
```

## Deployment (GitHub Pages)

1. Push to `main`.
2. On GitHub → this repo → **Settings → Pages**.
3. **Source**: Deploy from a branch → **main** / **(root)** → Save.
4. Wait ~60s; your site is live at `https://steph-dove.github.io/klausify-desktop-feedback/`.

Optional — custom domain:
1. Add a `CNAME` file in the repo root containing just the domain (e.g. `klaussy.app`).
2. Add a DNS CNAME record pointing `klaussy.app` at `steph-dove.github.io`.
3. Enable HTTPS in the Pages settings after the DNS propagates.

## Placeholders to fill before shipping

Search `index.html` for `{{…}}` markers:
- `{{DISCORD_INVITE_URL}}` — your Discord server invite link
- `{{COMPANY_NAME}}` — legal entity name (used in footer copyright)
- `{{YEAR}}` — current year

A quick one-liner to patch them (run from the repo root):

```bash
sed -i '' \
  -e 's|{{DISCORD_INVITE_URL}}|https://discord.gg/YOUR_INVITE|g' \
  -e 's|{{COMPANY_NAME}}|Stephanie Dover|g' \
  -e "s|{{YEAR}}|$(date +%Y)|g" \
  index.html
```

## Privacy & EULA pages

`privacy.html` and `eula.html` are linked from the footer. Generate from the source Markdown in the app repo (`klausify-desktop/docs/{PRIVACY,EULA}.md`) once they've been through legal review — any Markdown-to-HTML converter works, or a static wrapper with `<article>` around the raw text.

Pull-request templates for this repo can be added later under `.github/ISSUE_TEMPLATE/`.
