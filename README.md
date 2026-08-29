# catalyst-feed

Backup update feed for Catalyst Studio (static `latest.json` mirror).

- Primary feed: `https://chat.julykaoyan.xyz/catalyst-release/latest.json`
- Backup feed (this repo): `https://raw.githubusercontent.com/xiuxiudebobo/catalyst-feed/main/latest.json`

The Tauri updater tries endpoints in order and only falls through on a
non-2xx response, so the primary is always preferred. This mirror exists so
update **checks** keep working if the primary host is unreachable. Installer
downloads always come from the URLs inside `latest.json` (the primary host).

Update procedure (each release, after the primary feed is cut over):

```bash
scripts/release/publish-feed-backup.sh
```

This file contains version metadata and minisign updater signatures only —
no secrets.
