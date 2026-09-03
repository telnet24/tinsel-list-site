# Deploying the Tinsel List site

Static HTML on GitHub Pages, same pattern as border-builder-site. Three hand-authored pages (`index.html`, `privacy.html`, `support.html`); nothing is generated.

## Pages URL (live immediately)

The repo serves at `https://telnet24.github.io/tinsel-list-site/` as soon as Pages is enabled. That URL is already valid for the App Store Connect privacy-policy and support fields; swap in the custom domain later without resubmitting.

## Custom domain

### Buy it
Suggested names, in preference order: `tinsellist.app` (matches the bundle id `com.tinsellist`; `.app` forces HTTPS, which Pages provides), `tinsellistapp.com`, `gettinsellist.com`. Registrars: Cloudflare Registrar (at-cost), Porkbun, Namecheap (~$10-15/yr).

### Point it at GitHub Pages
At the registrar's DNS:
- Apex (`tinsellist.app`): four A records to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and four AAAA records to `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`.
- `www`: one CNAME to `telnet24.github.io`.

Then in the repo: Settings, Pages, Custom domain, enter the domain, save (this commits a `CNAME` file), and tick Enforce HTTPS once the certificate issues (minutes to ~24h).

### After the domain is live
- Update the privacy-policy and support URLs in App Store Connect.
- Update the in-app Settings privacy-policy link to the domain URL.
- Add `<link rel="canonical">` tags if the site ever grows content pages worth indexing; three utility pages do not need Search Console.
