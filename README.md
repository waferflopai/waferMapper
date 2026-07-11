# ⧉ waferMapper

**Merge CSV to Master Schema – Free ETL Tool**  
Map multiple incoming CSV files to a single master schema, visually. No uploads, no sign‑ups, no server – everything runs in your browser.

[![Live Demo](https://img.shields.io/badge/demo-vercel-blue?style=flat-square)](https://wafermapper.vercel.app/)
[![Built with](https://img.shields.io/badge/built%20with-vanilla%20JS%20%2B%20CSS-yellow?style=flat-square)](https://developer.mozilla.org/)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

---

## ✨ Features

- **Master & Incoming** – Define a master schema (CSV) and upload any number of incoming CSV files.
- **Visual Column Mapping** – Drag‑and‑drop columns from the incoming file to the master schema inside the modal.
- **Smart Transformations** – Apply transformations (trim, upper, lower, concat) to incoming values before merging.
- **Real‑time Preview** – See mapped rows instantly in the modal’s SQL panel.
- **SQL Generation** – Generate `CREATE TABLE` + `INSERT` statements from your mappings.
- **Presets** – Save and reuse mappings for recurring imports.
- **Undo / Redo** – Full history with keyboard shortcuts (`Ctrl+Z` / `Ctrl+Y`).
- **Export**  
  - Export merged data as CSV, JSON, or plain text.  
  - Export generated SQL.  
- **No Uploads** – All processing stays client‑side. Your data never leaves your machine.
- **Responsive** – Works on desktop and mobile.

---

## 🚀 Live Demo

Try it now: [waferMapper on Vercel](https://wafermapper.vercel.app/)

---

## 📖 How to Use

1. **Set up your master schema**  
   - Click the **“master → new”** button or upload a CSV with the “master” file input.  
   - If you create a new master, you’ll be prompted for a name and a comma‑separated list of columns.

2. **Add incoming files**  
   - Click the **“incoming → new”** button (to create an empty file) or upload one or more CSV files.  
   - Each incoming file appears as a node orbiting the master in the main workspace.

3. **Map columns**  
   - Click the **“+”** button on any incoming node to open the mapping modal.  
   - Inside the modal, drag a column from the incoming table and drop it onto a column in the master table.  
   - A mapping pill appears, showing the source → target relationship.  
   - Click the **“✕”** on a pill to remove all mappings to that target column.

4. **Apply transformations**  
   - Each mapping can include a transformation: `none`, `trim`, `upper`, `lower`, or `concat` (when multiple source columns map to the same target).  
   - The transformation is applied during export and SQL generation.

5. **Preview and run**  
   - Click **“⚡ gen”** to generate SQL for the current mappings.  
   - Click **“▶ run”** to preview the mapped data (first 5 rows) directly in the SQL panel.

6. **Export**  
   - Use the **“export all”** button (top‑right) to download all mapped files in your chosen format (CSV, JSON, or TXT).  
   - Within the modal, you can export **CSV** or **SQL** for the current file.

7. **Save presets**  
   - After defining mappings, click **“preset”** in the modal footer to save the mapping set.  
   - Presets are stored in your browser’s localStorage and can be reused later.

8. **Clear or undo**  
   - Use the **“clear”** button to reset everything.  
   - Use **“↩”** / **“↪”** or `Ctrl+Z` / `Ctrl+Y` to undo/redo any action.

---

## 📂 Data Formats

### Master CSV
The master file defines the target columns. Each row represents an entry in the final merged dataset.

### Incoming CSV
Each incoming file can have different columns. You map its columns to the master’s columns.

### Exported Merger
- **CSV** – A single CSV with all mapped rows from all incoming files, using the master’s columns.  
- **JSON** – An array of objects, each containing the mapped data per file and a `sourceFile` property.  
- **TXT** – A plain text dump with a separator for each file’s mapped CSV.

### Generated SQL
`CREATE TABLE` + `INSERT` statements for the mapped data, using the master’s column names.

---

## 💾 Data Persistence

- **Presets** are saved in `localStorage` under `csvMapper_presets`.  
- **Mappings, master data, and incoming files** are kept in memory while the page is open. Refreshing the page will lose the current session unless you export your work.

---

## 🛠️ Development

This is a single‑page HTML application – no build tools, no dependencies.  
To run locally:

1. Clone the repository:
   ```bash
   git clone https://github.com/waferflopai/waferMapper.git
   cd waferMapper
