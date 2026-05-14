# Phuket Harbour Website

Landing page for **Phuket Harbour** — Phuket's local ferry and island tour operator since 1994.

## Stack

Vanilla HTML + CSS + JS, single file. No framework, no build step.

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_ORG/phuket-harbour.git
cd phuket-harbour
```

### 2. Add video files

The 6 hero background videos are tracked via **Git LFS**. If you have LFS installed, they pull automatically:

```bash
git lfs pull
```

If you don't use LFS, manually copy the MP4 files into `assets/videos/`. The filenames must match exactly:

```
pexels-maksim-romashkin-12762099 (2160p).mp4
pexels-silent-sightseer-11720101 (Original).mp4
production_id_5147338 (1080p).mp4
pexels-francesco-navarro-6216472 (1080p).mp4
pexels-ibrahim-bennett-18110059 (2160p).mp4
pexels-maksim-romashkin-12762055 (2160p).mp4
```

### 3. Add the logo

Place `logo-white.png` (white version of the Phuket Harbour logo) in `assets/images/`.

### 4. Open locally

Just open `index.html` in a browser. No server needed for development.

For video autoplay to work in Chrome, open via a local server instead of `file://`:

```bash
# Python 3
python -m http.server 8080
# then open http://localhost:8080
```

## Before Going Live

Search for `66XXXXXXXXX` and replace all 5 occurrences with the real WhatsApp number.

Search for `pkey_test_YOUR_OMISE_PUBLIC_KEY` and replace with your Omise live public key.

Implement `chargeWithToken()` in the script block — it currently stubs the confirmation screen. Wire it to a server-side endpoint that calls the Omise Charges API.

Update the canonical URL, `og:image`, and footer social links.

## Project Structure

```
phuket-harbour/
├── index.html          ← entire site
├── assets/
│   ├── videos/         ← hero background MP4s (Git LFS)
│   └── images/         ← logo-white.png
├── .gitignore
├── .gitattributes      ← Git LFS config for media files
├── .cursorrules        ← Cursor AI context (design tokens, section map, rules)
└── README.md
```

## First-Time GitHub Push

```bash
# Install Git LFS (once, system-wide)
git lfs install

# Initialise repo
cd phuket-harbour
git init
git lfs track "*.mp4" "*.png" "*.jpg"   # already in .gitattributes
git add .
git commit -m "Initial commit"

# Push to GitHub
git remote add origin https://github.com/YOUR_ORG/phuket-harbour.git
git branch -M main
git push -u origin main
```
