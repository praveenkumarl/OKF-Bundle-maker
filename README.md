<div align="center">

# 📚 OKF Bundle Maker

**Turn any document into an Open Knowledge Format (OKF) bundle, then learn from it.**
Drop in a PDF, Word file, text or Markdown. Get clean, linked knowledge files and a study chat with quizzes and flashcards.

[![Single file](https://img.shields.io/badge/single-HTML%20file-0f766e)](#-quick-start)
[![No server](https://img.shields.io/badge/no-server%20%7C%20no%20upload-0f766e)](#-privacy)
[![OKF](https://img.shields.io/badge/OKF-v0.2-0f766e)](#-what-is-okf)
[![AI optional](https://img.shields.io/badge/AI-optional-0f766e)](#-optional-ai-mode)

[Quick start](#-quick-start) · [How to use](#-how-to-use) · [AI mode](#-optional-ai-mode) · [Output](#-what-you-get) · [FAQ](#-faq) · [Developers](#-for-developers)

</div>

---

## ✨ What it does

| | |
|---|---|
| 📄 **Reads your documents** | PDF, Word (`.docx`), TXT, Markdown, HTML, CSV |
| 🧩 **Splits them into concepts** | Finds headings, lists and tables, and cuts the text into small titled topics |
| 📦 **Builds an OKF v0.2 bundle** | One Markdown file per concept, with a YAML header, an `index.md`, a `log.md` and "See also" links |
| ⬇️ **Downloads as a `.zip`** | Includes your original files under `references/` |
| 💬 **Lets you study it** | Ask questions, see an outline, compare topics, take quizzes, flip flashcards |
| 🤖 **Optional AI mode** | Plug in your own API key for real explanations, smarter search and better quizzes |

Everything runs **in your browser**. There is nothing to install and no account to create.

---

## 🚀 Quick start

**Option 1. Use it online** (GitHub Pages)

1. Open the live page: `https://<your-username>.github.io/<repo-name>/`
2. Drop a file onto the page.
3. Click **Download bundle (.zip)**.

**Option 2. Use it offline**

1. Download `index.html` from this repo (or the release page).
2. Double-click it. It opens in any modern browser (Chrome or Edge recommended).
3. That's it. The file is fully self-contained, including the PDF and zip libraries.

> 💡 The page opens with a small built-in example already loaded, so you can try every feature before adding your own files.

---

## 🧭 How to use

The page has three tabs: **Build**, **Learn** and **Bundle**.

### 1. Build: create the bundle

1. **Add documents.** Drop files on the box, click to choose files, or use **Paste text instead**. Add several files to get one bundle with a folder per file.
2. **Shape the bundle** (optional). The defaults work for most documents.

   | Option | What it does |
   |---|---|
   | **Bundle name** | Title of the front page (`index.md`) and the zip file name. |
   | **Concept size** | How finely the document is cut. A smaller number gives fewer, longer concepts (whole chapters). A larger number gives more, shorter ones (down to sub-sections). *Automatic* picks a sensible level. |
   | **Concept type** | A label saved in each file's header as `type`. It says what kind of knowledge the file holds, for example `Reference`, `Lesson`, `Glossary`, `Policy` or `Playbook`. Leave it empty and the tool chooses per file: **Overview** for a section intro, **List** for mostly bullets, **Table** for tables, otherwise **Reference**. Type your own word to give every concept the same type. |
   | **Extra tags** | Keywords added to every file's `tags`, on top of the automatic ones. |
   | **Link related concepts** | Adds a "See also" list where one concept mentions another by title. |

3. **Review and save.** Untick a row to leave a concept out, or rename its title. Then click **Download bundle (.zip)**.

### 2. Learn: study from your bundle

Click **Study this bundle** (or the **Learn** tab) and try:

| Type this | You get |
|---|---|
| `which cloud brings thunder` | The matching sections, with your words highlighted |
| `outline` | The structure of everything you loaded |
| `Moon vs Sun` | A side-by-side comparison of two concepts |
| `quiz` or `quiz clouds` | Multiple-choice questions, optionally on one topic |
| `flashcards` or `flashcards clouds` | Flip cards, optionally on one topic |
| `help` | A reminder of what you can ask |

Click a topic in the left rail to open it directly.

Without AI, quizzes ask *"Which term fits this description?"* and *fill-in-the-blank* questions built from your text. Chapter and section numbers are removed from titles, and questions never ask about headings.

### 3. Bundle: inspect the files

See the file tree, read any generated file exactly as it will be saved, and copy it with **Copy file**.

---

## 🤖 Optional AI mode

Keyword search is fast but literal. Turn on **AI mode** in the Learn tab for:

- 💡 **Real explanations** in your own language, with clickable citations to the concepts used
- 🔎 **Smarter search**: ask full questions, not just keywords
- 📝 **Better quizzes and flashcards** written by the model, on any topic
- 🧾 **Summaries**: type `summary`
- 🔁 **Follow-ups**: "explain that more simply"

Large documents are handled by first picking the relevant sections, so a whole book does not have to fit in one request.

### Set it up

1. Open the Learn tab, then click **AI settings**.
2. Pick a provider, paste your API key, and optionally set the model name.
3. Click **Test**, then **Save and turn on**.

| Provider | Notes |
|---|---|
| **Claude (built-in)** | No key needed. Only on the hosted Claude page, where you approve it once. |
| **Anthropic API** | Your key. Default model `claude-sonnet-5-5`. |
| **OpenAI** | Your key. |
| **Google Gemini** | Your key, through its OpenAI-compatible address. |
| **OpenRouter** | Your key. Access to many models. |
| **Groq** | Your key. |
| **DeepInfra** | Your key. Use the exact model name from their model list. |
| **Ollama** | Free, runs on your own computer. Nothing leaves your machine. Start Ollama with browser access allowed (`OLLAMA_ORIGINS`). |
| **Other (OpenAI-compatible)** | Enter any base URL, such as `https://host/v1`. |

**Tips**

- Use a model that follows instructions well. Quizzes and flashcards need valid JSON back, and very small models sometimes fail at it. If you see *"No usable questions"*, click **New quiz** or try a larger model.
- Tick **Remember the key on this device** only on a computer you trust. Otherwise the key stays in memory until you close the tab.
- Some provider endpoints may block calls from web pages. If connecting fails, use the downloaded `index.html` copy or a provider known to allow browser access.

---

## 📦 What you get

Example output for a document called *Weather and Water Basics*:

```
weather-and-water-basics-okf.zip
├── index.md                  ← front page (okf_version: "0.2")
├── log.md                    ← what was generated and when
├── overview.md
├── the-water-cycle/
│   ├── index.md
│   ├── overview.md
│   ├── evaporation.md
│   └── condensation.md
├── clouds/
│   ├── cumulus.md
│   └── stratus.md
├── weather-instruments.md
└── references/
    └── weather-notes.md      ← your original file
```

Each concept file looks like this:

```markdown
---
type: "Reference"
title: "Cumulus"
description: "Cumulus clouds are puffy and white with flat bases."
tags: [clouds, cumulus]
generated: { by: okf-bundle-maker/0.1, at: 2026-10-14T10:00:00Z }
status: draft
sources:
  - id: src
    resource: /references/weather-notes.md
    title: "weather-notes.md"
---

# Cumulus

Part of [Clouds](/clouds/index.md). Source: weather-notes.md.[^src]

Cumulus clouds are puffy and white with flat bases. They usually mean fair weather.

# See also

* [Stratus](/clouds/stratus.md)

[^src]: weather-notes.md
```

Files start as `status: draft`, because they are generated by a program and should be reviewed before you treat them as verified.

---

## 🧠 What is OKF?

**Open Knowledge Format** is a simple way to keep knowledge as a folder of Markdown files. Each file is one concept with a small YAML header. Only `type` is required. `title`, `description`, `tags` and `sources` are recommended. Files link to each other with ordinary Markdown links, and two reserved files, `index.md` and `log.md`, describe the folder.

Because it is only Markdown and folders, an OKF bundle works in any editor, any Git repo, and any tool or AI assistant that can read files.

---

## 🔒 Privacy

- **Your files never leave your device.** Reading, splitting and the Learn tab all run locally in the browser.
- **Only AI mode sends text**, and only to the provider you choose. It sends the excerpts needed for each question, not the whole library.
- API keys go straight from your browser to the provider. This project has no server and collects nothing.

---

## ⚠️ Good to know

| Situation | What to do |
|---|---|
| **Scanned PDF** (pages are images) | The tool cannot read images. Run OCR first, or paste the text. |
| **Old `.doc` file** | Open it in Word and *Save as* `.docx`. |
| **PDF with odd or garbled characters** | This usually means a legacy font. Copy the text from a PDF viewer and use **Paste text**. |
| **Multi-column PDF** | Text can interleave. Paste or convert it to Word first if the result looks mixed. |
| **Very large PDF** | The first 600 pages are read. |
| **No headings in your file** | It still works. The tool looks for short title-like lines, numbered headings and ALL-CAPS lines, and otherwise cuts the text into parts. |
| **Quiz says there is not enough text** | Without AI, quizzes need definition-style text such as "Term: explanation" or "X is …". Turn on AI mode for better questions. |

Matching is word-based (it understands simple word endings), not meaning-based. AI mode adds meaning.

---

## ❓ FAQ

**Is it free?** Yes. The tool is free. AI mode uses your own provider account, which may have its own costs. Ollama is free.

**Does it need internet?** The page itself works offline once downloaded. Only AI providers need a connection (Ollama runs locally).

**Can I use it with languages other than English?** Yes. Text reading and matching are Unicode-aware, and it has been tried with Tamil. AI mode answers in the language you write in.

**Why are my concept titles different from my headings?** The tool removes numbering like "Chapter 3:" or "1.2" so topics read cleanly. You can rename any title before you download.

**Can I edit the output?** Yes. They are plain Markdown files. Edit them in any editor, then change `status` from `draft` once reviewed.

**Where do I put the bundle afterwards?** Anywhere files go: a Git repo, a notes app, a shared drive, or a folder an AI assistant can read.

---

## 🛠 For developers

The release is one self-contained HTML file. Source lives in modules and is joined by a small script.

```
.
├── template.html        UI, styles and wiring
├── assemble.py          joins everything into one HTML file
├── lib/
│   ├── text.js          tokenising, slugs, sentence splitting
│   ├── blocks.js        text/Markdown → blocks, heading detection and cleanup
│   ├── structure.js     blocks → section tree → concepts
│   ├── render.js        concepts → OKF files (frontmatter, index, log)
│   ├── study.js         search, outline, compare, quiz, flashcards
│   ├── readers.js       PDF, DOCX, HTML, CSV, TXT, MD readers
│   ├── llm.js           optional AI providers, routing and prompts
│   └── sample.md        built-in example
├── test_core.js         core pipeline test (Node)
└── test_llm.js          AI layer test with mocked responses (Node)
```

**Build**

```bash
npm install                                     # pdfjs-dist@3.11.174 and jszip@3.10.1
python3 assemble.py index.html                  # writes the single-file tool
```

**Test**

```bash
node test_core.js
node test_llm.js
```

**How it works**

1. A **reader** turns each file into a list of blocks: headings, list items, paragraphs, tables and code.
2. Heading rules fix up the structure: label headings, ALL-CAPS lines, numbered headings, PDF font sizes, running headers and footers, and book numbering.
3. A **section tree** is cut into concepts at the chosen depth.
4. The **renderer** writes OKF v0.2 Markdown, folder indexes, a root `index.md` with `okf_version: "0.2"`, and `log.md`.
5. The **study engine** loads the generated bundle itself, so what you study is exactly what you download.

**Libraries**: [pdf.js](https://mozilla.github.io/pdf.js/) for PDFs and [JSZip](https://stuk.github.io/jszip/) for Word files and the zip download. Both are inlined, so the page makes no network requests unless AI mode is on.

**Publish with GitHub Pages**: put the built file at the repo root as `index.html`, then go to *Settings → Pages* and deploy from the main branch.

---

## 🤝 Contributing

Ideas and fixes are welcome.

- 🐛 **Found a bad split?** Open an issue with the heading text (not the whole document) and what you expected.
- 🌍 **Another language or file layout?** Share a short anonymised sample.
- 🔌 **Another AI provider?** Providers are small entries in `lib/llm.js`. Anything OpenAI-compatible needs only a base URL and default model.

## 📄 License

Choose a license for your repo (MIT is a common, permissive choice) and add a `LICENSE` file.

<div align="center">

Made for learners who would rather study a topic than hunt through a PDF. 📖

</div>
