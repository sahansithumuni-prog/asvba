# ASVBA Sinhala – website (v1.0)

Pages: **Home · Generator · About · Contact · Sign In** (one file, `index.html`; the pages are `#/home`, `#/generator`, `#/about`, `#/contact`).
The AI models are **not** in this website – they run in the Kaggle notebook `ASVBA_WebApp_v0.4_Kaggle.ipynb` (the "AI studio").
The repository is public, so no keys or passwords go here.

```
index.html                    the whole website
config.json                   backend_url (studio link), contact_email
assets/hero.jpg               Home page picture
assets/characters.json        the 5 AI ambassadors: name, voice, pictures
assets/characters/*.jpg       character pictures
```

## 1. Put it online (once) – GitHub Pages
1. github.com → **New repository** → `asvba` → **Public** → Create.
2. **Add file → Upload files** → drag the whole folder content (`index.html`, `config.json`, `README.md` and the `assets` folder) → **Commit changes**.
3. **Settings → Pages** → Source **Deploy from a branch** → `main` / `(root)` → **Save** → `https://<username>.github.io/asvba/`
4. Test without the studio: `https://<username>.github.io/asvba/?mock=1#/generator` → Sign In → code `demo`.

Vercel: Add New → Project → import `asvba` → Framework **Other** → Deploy.

## 2. Things to set
- `config.json` → `"contact_email"`: the group's email for the Contact page (opens the visitor's email app). Empty = the page says the address is not set.
- `config.json` → `"backend_url"`: written automatically by the Kaggle notebook (secrets `GITHUB_TOKEN` + `ASVBA_SITE_REPO`), or paste the `https://….gradio.live` link by hand each session. The notebook keeps `contact_email` when it updates the file.
- **About page → team / supervisor names:** in `index.html` search for `Team members and supervisor can be added here`.

## 3. Characters (IMPORTANT before real videos)
The 5 character pictures now are **small crops from the design mock-up (about 140 px)** – fine as thumbnails, **too small for SadTalker** (blurry face in the video).
For every character make one high-resolution AI-generated picture (same person, same clothes):
- about **1024 × 1024 px**, waist-up, face to the camera, mouth closed, plain background, good light;
- save as `assets/characters/<id>_avatar.jpg` and change `"avatar"` in `assets/characters.json` to that file;
- `"voice"`: `F1 - female voice`, `F2 - female voice`, `M1 - male voice` or `M2 - male voice`;
- only AI-generated people – never a photo of a real person. The CLS (cultural localisation) results decide the final look.

`assets/hero.jpg` is also cut from the mock-up (802 × 548 px). A sharper version (about 1600 × 1100 px, same picture) can replace it.

## 4. How a client makes a video
1. **Ad Brief** → **Generate Script** (only the brief is sent; Llama-3-Sinhala draft → Gemini script).
2. **Review Script** → change any word → name in "Reviewed by" → **Confirm Script** (the text is locked; "Edit again" unlocks it).
3. **Select Character** (or **Your own** AI avatar) → 4. **Upload Product Image** (+ optional logo) → tick the confirmation.
5. **Create** → the confirmed script goes to SinhalaVITS (voice of the chosen character) → SadTalker → LatentSync → ad → **Download 9:16** (Reels/Shorts) or **16:9** (YouTube).
Language = Sinhala; length = from the brief (30 s if not stated); both formats are made every time.
If the page closes during the video: open it again, Sign In, **Show it**.

## 5. Each studio session (team)
Kaggle → `ASVBA_WebApp_v0.4_Kaggle.ipynb` → GPU T4 x2, Internet On, Secrets `GEMINI_API_KEY`, `HF_TOKEN`, `ASVBA_APP_PASSWORD` (+ `GITHUB_TOKEN`, `ASVBA_SITE_REPO`) → **Run All** → keep the tab open (max 12 h) → Stop session when finished.
