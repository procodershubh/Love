# ✦ Love Quest — A 5-Level Romantic Game

A modern, animated, level-based romantic web app. **5 distinct mini-games** on a glowing
path map — unlock them in order, reach the final surprise: a typewriter love letter on an
unrolling parchment scroll, followed by a photo gallery of you two, with confetti showers.

Built with **GSAP** for smooth animations, **canvas-confetti** for celebration, **Howler.js**
for audio (with a built-in Web-Audio synth fallback so it works even with no sound files), and
**Unsplash** for instant gorgeous backgrounds.

---

## 🎮 The 5 levels

| # | Name | Game type |
|---|------|-----------|
| 1 | **Word Whisper** | Type the secret nickname (names are configurable — see below) |
| 2 | **Memory Match** | Flip-card matching · 16 cards, 8 pairs, timer + moves counter |
| 3 | **Photo Puzzle** | 3×3 drag-and-drop jigsaw with real tabs/notches · pieces snap into place |
| 4 | **Heart Rain** | Tap 15 falling pink hearts in 35s · a big central heart fills as you score |
| 5 | **Constellation of Love** | Tap the glowing stars in order to draw a heart constellation |

**Each level must be completed in order** — locked levels can't be opened.
A glowing path on the map fills in as she progresses, a mascot bunny hops forward, and
stones turn green ✓ when done.

When all 5 are done, the **"Open Surprise"** button activates → confetti everywhere, a
parchment love letter types itself out, then a gallery of your photos.

---

## 📁 Folder structure

```
love-quest/
├── index.html
├── .gitignore
├── css/style.css
├── js/app.js              ← game logic (no need to touch)
└── assets/
    ├── config.json        ← edit YOUR settings here (names, hints)
    ├── images/
    │   ├── memories/
    │   │   ├── memory-1.JPG     ← Your couple photo 1 (square)
    │   │   ├── memory-2.JPG     ← Your couple photo 2
    │   │   ├── memory-3.jpeg    ← Your couple photo 3
    │   │   ├── memory-4.jpeg    ← Your couple photo 4
    │   │   ├── memory-5.jpeg    ← Your couple photo 5
    │   │   └── memory-6.jpeg    ← Your couple photo 6
    │   │
    │   └── puzzle/
    │       └── puzzle.png       ← One special photo for the jigsaw (square)
    │
    └── sounds/                  ← All optional
        ├── bgm.mp3
        ├── click.mp3
        ├── correct.mp3
        ├── wrong.mp3
        ├── sparkle.mp3
        └── reveal.mp3
```

---

## ✏️ Customizing (the easy way) — `assets/config.json`

Open **`assets/config.json`** and edit the values there. You don't have to touch `app.js`.
Refresh the page after saving.

```json
{
  "allowedNames": ["love","honey",....],
  "level1Hint": "💡 hint: starts with \"p\" or \"ch\"..."
}
```

- **Add a name** → just add another `"name"` to the `allowedNames` list (keep the commas,
  and don't put a comma after the last one — that's the one JSON rule to remember).
- The game ignores capital letters, spaces and punctuation when checking, and also matches
  if her answer *contains* one of the names — so you can be generous here.
- The config is loaded with `fetch`, so **run the site over a local server** (see *How to run*).
  If it can't be loaded (e.g. opening `index.html` directly via `file://`), the game safely
  falls back to its built-in defaults.

### Other tweaks (in `js/app.js`)

| What | Where |
|------|-------|
| The love letter text | `LOVE_LETTER` (the string `[NAME]` is replaced with her name) |
| Letter sign-off | `LETTER_SIGN` |
| Gallery photos + captions | `GALLERY` array |
| Heart Rain difficulty | `RAIN_TARGET = 15` (hearts needed), `RAIN_TIME = 35` (seconds) |
| Level instructions text | `INSTRUCTIONS` object |

### Change Unsplash backgrounds

`index.html`, find any `images.unsplash.com` URL and swap it. Format:
```
https://images.unsplash.com/photo-XXXXXX?auto=format&fit=crop&w=1920&q=80
```

---

## 🎨 Where photos go

**Scene backgrounds** are pulled from Unsplash directly — no work needed, they just load.

**Your couple photos:**
- `assets/images/memories/memory-1` … `memory-6` — square crops work best
  (the app expects `memory-1.JPG`, `memory-2.JPG`, then `memory-3.jpeg`…`memory-6.jpeg`;
  rename your files to match, or update the `GALLERY` array in `js/app.js`)
- `assets/images/puzzle/puzzle.png` — the photo cut into the 3×3 jigsaw

If you don't add photos, beautiful placeholders show instead — the site fully works without them.

---

## 🔒 Photos & privacy — `.gitignore`

This repo ships with a `.gitignore` so **your personal photos are never committed/pushed**:

```
assets/images/memories/*
assets/images/puzzle/*
assets/sounds/*.mp3
```

The folders are kept (via `.gitkeep` files) but the images inside them stay local and private.
If you *do* want to commit a specific photo, either remove its line from `.gitignore` or
force-add it: `git add -f assets/images/puzzle/puzzle.png`.

---

## 🎵 Sound files (optional)

Drop these into `assets/sounds/`. If files are missing, the site **auto-generates synth tones**
with the Web Audio API — so it sounds great either way.

| File | Suggested mood |
|------|----------------|
| `bgm.mp3` | Soft piano — *Pixabay → search "romantic piano"* |
| `click.mp3` | Short pop |
| `correct.mp3` | Warm chime |
| `wrong.mp3` | Gentle dip |
| `sparkle.mp3` | Twinkle |
| `reveal.mp3` | Magical whoosh |

Free sources: [pixabay.com/sound-effects](https://pixabay.com/sound-effects/) · [freesound.org](https://freesound.org)

---

## ▶️ How to run

1. (Optional) Drop your photos in the right folders and edit `js/config.js`
2. Open `index.html` in any modern browser

For best results (some browsers need a server for audio + Unsplash CORS):
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

---

## 🛠 Libraries (all from CDN — no install needed)

- [GSAP 3.12](https://gsap.com) — smooth animations
- [canvas-confetti](https://github.com/catdad/canvas-confetti) — the final burst
- [Howler.js](https://howlerjs.com) — audio
- Google Fonts: **Fraunces** (display), **Inter** (UI), **Caveat** / **Dancing Script** (handwritten accents)
- Unsplash for backgrounds

---

She's going to love it. 💗
