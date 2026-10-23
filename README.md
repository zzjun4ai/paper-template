# paper-template

This repository contains a small LaTeX paper template with separate entry files for the main manuscript and supplementary information.

## Structure

- `common/preamble.tex`: shared packages, formatting, caption, bibliography, and hyperlink settings.
- `manuscript/manuscript.tex`: main paper entry file.
- `manuscript/references.bib`: bibliography for the main paper.
- `manuscript/figures/`: figures used by the main paper.
- `supplementary/supplementary.tex`: supplementary information entry file.
- `supplementary/references.bib`: bibliography for the supplement.
- `supplementary/figures/`: supplementary figures.

## Compile

Use a LaTeX distribution such as TeX Live or MiKTeX with `latexmk`, pdfLaTeX, and BibTeX available. Install the packages loaded by `common/preamble.tex`, including `xltabular`, before compiling. With MiKTeX, enable automatic installation of missing packages or install them through MiKTeX Console; with TeX Live, install missing packages through `tlmgr`.

Compile from each entry file's directory so that relative paths resolve correctly.

```powershell
cd supplementary
latexmk -pdf supplementary.tex

cd ../manuscript
latexmk -pdf manuscript.tex
```

For cross-references from the manuscript to the supplement, compile the supplementary file first, then compile the manuscript.

## Cleanup

Generated LaTeX build files are ignored by `.gitignore`. To clean a directory after compiling:

```powershell
latexmk -c
```

Use `latexmk -C` only when you also want to remove the generated PDF.
