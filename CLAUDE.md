# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

LaTeX resumes based on the "Jake's Resume" template ([sb2nov/resume](https://github.com/sb2nov/resume/)).

- `base-form/resume.tex` — the pristine template with placeholder content; `base-form/resume.png` is its preview shown in the README. Don't put real content here — copy it when starting a new resume variant.
- `eng/qa-automation/resume.tex` — Pavel Kolyagin's QA Automation Engineer resume (English). New variants follow the same `<language>/<position>/resume.tex` layout.
- `ru/full/resume.tex` — the full Russian resume (Software Engineer — Internal Tools & AI). Cyrillic support in pdflatex comes from `\usepackage[T2A]{fontenc}` + `\usepackage[utf8]{inputenc}` + `babel` with `russian` — keep those when creating Russian variants.

## Building

Compile with pdflatex (a full TeX Live install is available at `/Library/TeX/texbin`), from the directory of the resume being built:

```sh
cd eng/qa-automation
pdflatex resume.tex
```

Or use latexmk for automatic reruns and cleanup:

```sh
latexmk -pdf resume.tex
latexmk -c   # clean aux files
```

There are no tests or linters.

## Structure of resume.tex

- **Preamble** defines custom commands that all content must use: `\resumeSubheading` (job/school entries), `\resumeProjectHeading` (project entries), `\resumeItem` (bullet points), and the `\resumeSubHeadingListStart`/`End` and `\resumeItemListStart`/`End` list wrappers. Edit content through these commands rather than raw LaTeX so spacing stays consistent.
- **Font options** are commented out in the `FONT OPTIONS` block near the top — uncomment one `\usepackage` line to switch fonts.
- `\pdfgentounicode=1` keeps the PDF machine-readable/ATS-parsable; don't remove it.
- Content sections follow in order: Heading, Education, Experience, Projects, Technical Skills.
