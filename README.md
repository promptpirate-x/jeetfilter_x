# 💩 JeetFilterX — X Jeet Filter (Pantone 448C Version)

> *"The ugliest colour in the world, now on the ugliest posts in your timeline."*

A Tampermonkey/Greasemonkey userscript that detects the **account country** of every post on X (Twitter), appends a **country flag** to usernames, and paints posts from third-world regions in glorious **[Pantone 448 C](https://en.wikipedia.org/wiki/Pantone_448_C)** — the colour officially deemed so repulsive it was chosen for cigarette packaging to discourage smoking. Same energy.

![Pantone 448 C swatch](https://img.shields.io/badge/Pantone_448_C-%234A412A?style=for-the-badge&logoColor=white)
![Platform](https://img.shields.io/badge/platform-X%20%2F%20Twitter-black?style=for-the-badge&logo=x)
![License](https://img.shields.io/badge/license-WTFPL-brightgreen?style=for-the-badge)

---

## ✨ Features

- **Country Detection** — Queries X's internal `AboutAccountQuery` API to resolve where each account is based.
- **Flag Injection** — Appends the account's country flag emoji (🇮🇳 🇳🇬 🇵🇰 etc.) directly into the username area of every tweet.
- **Pantone 448 C Highlighting** — Posts from targeted regions get a distinctive brown overlay (`#4A412A`) with gold-coloured links for readability.
- **Blacklist / Whitelist Mode** — Built-in filter panel (accessible from the sidebar) lets you hide or exclusively show posts by country.
- **Persistent Cache** — Uses IndexedDB to cache country lookups so repeated visits are instant.
- **Rate-Limit Aware** — Automatic exponential backoff on 429 responses. Set it and forget it.
- **MutationObserver Powered** — Picks up new tweets as they load, including infinite scroll and navigation.

---

## 📸 Screenshots

| Highlighted Timeline | Filter Sidebar |
|---|---|
| Posts from targeted regions glow in the unmistakable hue of Pantone 448 C with gold links. | A `Filters` button is injected into X's navigation sidebar for quick access. |

---

## 🚀 Installation

### Prerequisites

You need a userscript manager extension installed in your browser:

| Browser | Extension |
|---|---|
| Chrome / Edge / Brave | [Tampermonkey](https://www.tampermonkey.net/) |
| Firefox | [Tampermonkey](https://www.tampermonkey.net/) or [Greasemonkey](https://www.greasespot.net/) |
| Safari | [Userscripts](https://apps.apple.com/us/app/userscripts/id1463298887) |

### Install the Script

1. Open your userscript manager dashboard.
2. Create a new script.
3. Paste the contents of **`jeetfilterx.user.js`** and save.
4. Navigate to [x.com](https://x.com) — the script activates automatically.

---

## ⚙️ Configuration

### Highlighted Regions

The script highlights posts from accounts based in the following regions by default:

**South Asia** — India, Bangladesh, Pakistan, Nepal, Sri Lanka, Bhutan, Maldives, Afghanistan

**Africa** — Nigeria, Kenya, South Africa, Ghana, Ethiopia, Tanzania, Uganda, Congo, Egypt, Morocco, Algeria, Sudan, Angola, Mozambique, Madagascar, Cameroon, Côte d'Ivoire, Niger, Burkina Faso, Mali, Malawi, Zambia, Senegal, Chad, Somalia, Zimbabwe, Guinea, Rwanda, Benin, Burundi, Togo, Sierra Leone, Libya, Central African Republic, Mauritania, Eritrea, Namibia, Gambia, Botswana, Gabon, Lesotho, Guinea-Bissau, Equatorial Guinea, Mauritius, Eswatini, Djibouti, Comoros, Cape Verde, Seychelles, São Tomé and Príncipe

**Meta-regions** — "Africa", "South Asia", "Sub-Saharan", "Third World", "Developing"

To modify the list, edit the `highlightTerms` array inside `applyCountry()`.

### Blacklist / Whitelist Filter

Click the **Filters** button in X's left sidebar to open the filter panel:

| Option | Description |
|---|---|
| **Enable filter** | Toggle filtering on/off. |
| **Filter entries** | One country or keyword per line. |
| **Blacklist mode** | Hides posts matching your entries. |
| **Whitelist mode** | Shows *only* posts matching your entries. |

Settings persist in `localStorage` across sessions.

---

## 🎨 The Colour

**Pantone 448 C** (`#4A412A`) was selected by market research firm GfK Bluemoon as the world's ugliest colour. The Australian government adopted it for plain tobacco packaging in 2012 to make cigarettes less appealing. It has since been adopted by the EU, UK, and other countries for the same purpose.

We repurposed it here because it felt appropriate.

---

## 🛠️ Technical Details

- **API Endpoint** — `https://x.com/i/api/graphql/.../AboutAccountQuery`
- **Auth** — Uses X's public bearer token + your session CSRF token (no additional login required).
- **Storage** — IndexedDB (`aboutAccountCache` database) for persistent country cache.
- **Rate Limiting** — 500ms minimum between requests, exponential backoff on 429s (up to 100 retries).
- **DOM Integration** — `MutationObserver` on `document` with `childList` + `subtree` for real-time tweet detection.

---

## 📝 Changelog

### v0.0.5
- Pantone 448 C highlighting for targeted regions
- Gold link colours for readability on highlighted posts
- Country flag emoji injection
- Blacklist/whitelist filter with sidebar UI
- IndexedDB caching
- Rate-limit handling with exponential backoff

---

## 🤝 Credits

- **Original Script** — [FilterX](https://codeberg.org/FilterX/FilterX) by `filterxdev@proton.me`
- **Pantone 448 C Modifications** — [@parrotpirate](https://x.com/parrotpirate)

---

## ⚠️ Disclaimer

This script uses X's internal GraphQL API, which is undocumented and subject to change. It may break at any time if X modifies their API structure, authentication, or rate limits. Use at your own risk.

---

## 📄 License

Do whatever you want with it. If you feel like donating, the original creator's contact is `filterxdev@proton.me`.
