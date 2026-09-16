# Black Code Blocks for Obsidian PDF Export

Two CSS snippets for Obsidian that turn the washed-out, light-gray code blocks in **Export to PDF** into clean **black, terminal-style blocks** — with readable white text and preserved syntax colors.

> Both snippets live inside `@media print`, so they **only affect the exported PDF (and physical printing)**. Your editor and reading view look exactly the same as before — that is by design.

---

## What's in this folder

| File | How it works | Best for |
|------|--------------|----------|
| **`Black-snippet.css`** | Forces the `pre` container to a solid black background (`#000000`), sets plain code text to white (`#e6e6e6`), and keeps your theme's own syntax-highlighting colors untouched (`print-color-adjust: exact` makes browsers print the background). | Dark themes, or themes whose code colors are already light |
| **`black-snippet-color.css`** | CSS filter trick: `invert(100%)` + `hue-rotate(180deg)` flips the whole block white → black, then rotates hues back so syntax colors stay natural. Also fixes the "white highlight" double-inversion bug and bolds tokens for extra contrast. | Default/light themes — the colors adapt to the black background automatically |

**Enable only ONE of the two at a time.** Both style the same `pre` / `code` elements; running both together gives unpredictable results.

---

## Proof — what they do to an exported PDF

Rendered from a simulated Obsidian note (default light theme) under print media — the same rendering path Obsidian's *Export to PDF* uses.

**1. Default export, no snippet — the problem: washed-out light-gray blocks**

[proof-1-default.png](https://github.com/suryansh3/Obsidian-black-snippet/blob/87a663d13465dfd5ae3129bf66c06bec723f377f/proof-1-default.png)

**2. With `Black-snippet.css` — solid black block, white plain text, theme syntax colors kept**

![Result with Black-snippet.css](images/proof-2-black-snippet.png)

**3. With `black-snippet-color.css` — block inverted white → black, syntax colors auto-adapted**

![Result with black-snippet-color.css](images/proof-3-color.png)

---

## Installation (Obsidian desktop)

1. Open Obsidian and go to **Settings → Appearance**.
2. Scroll down to the **CSS snippets** section.
3. Click the **folder icon** next to "CSS snippets" — this opens `<your-vault>/.obsidian/snippets/`.
4. Copy **`Black-snippet.css`** and/or **`black-snippet-color.css`** into that folder.
5. Back in **Settings → Appearance**, click the **refresh icon** next to "CSS snippets" — the file name(s) appear in the snippet list.
6. Toggle the snippet **ON**.

## Exporting the PDF

1. Open the note you want to export.
2. Open the **File menu → Export to PDF** (or run **"Export to PDF"** from the command palette).
3. The code blocks come out black — no other settings needed. The snippets force background printing (`print-color-adjust: exact`), so you don't need to touch any printer option.

---

## Troubleshooting

| Symptom | Fix |
|---------|-----|
| Code blocks are still light gray | Make sure the snippet is toggled **ON** in Settings → Appearance, and that you used **Export to PDF** — on screen nothing changes by design |
| The new snippet doesn't appear in the list | Click the **refresh icon** next to "CSS snippets", or restart Obsidian |
| Colors look wrong or double-applied | **Both** snippets are enabled — turn one off |
| Some syntax colors look dim on the black box (case 2 image) | `Black-snippet.css` keeps your theme's token colors verbatim; if your theme uses dark code colors (light theme), prefer **`black-snippet-color.css`**, which inverts them to fit the black background |
