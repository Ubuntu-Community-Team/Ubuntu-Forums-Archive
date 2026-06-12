---
title: "PDF Library"
date: 2008-01-17
forum: Programming Talk
---

### Post by skeeterbug on 2008-01-17
Hey,
Does anyone know of a good PDF manipulating library out there? I've been able to find libraries that create PDF files, but there don't seem to be many that work with existing PDF files. Specifically, I need to do some processing on URL/Links within the PDF files (not just standard page merging), and re-write them to a new PDF.

---

### Post by pmasiar on 2008-01-17
Thats a good question, same experience here. Most free libraries are for writing/merging/page manipulation of PDF, not to help parse existing one.

There are many closed-source libraries for sale, but it is hard to test how good they are, anyone has experience with it?

Best quick and dirty draft solution for parsing (for my need) was commandline utility pdftotext (included in Ubuntu), then manually parse resulting text file. Of course this way you will lose all formatting information. IIRC pdftotext can create HTML instead of text, so that might save you some formatting.

Another option is: Adobe website provided web service to convert PDF file to different format, but you need to write what platform you use, and why PDF reader is not available :-(

I cannot use that option, my file is huge: 900MB ... :-/

I need some way to get pictures out of that PDF, any suggestions?

---

### Post by wolfbone on 2008-01-18
pdfimages from poppler (or xpdf or somewhere) extracts images from PDFs.

---

### Post by skeeterbug on 2008-01-18
EDIT:

Nevermind, their sample mangled my PDF links. :-/

---

### Post by dwblas on 2008-01-18
There is pypdf.  Also, "python read pdf" at sourceforge yields 5716 hits, one of which is rsclib="Small Python library with various things such as Configuration file parsing (in Python syntax), HTML and PDF parsing. Used in others of my projects."  I haven't tried any of these but do use postscript and convert to pdf, so would appreciate it if you post back with any good solution.

---

