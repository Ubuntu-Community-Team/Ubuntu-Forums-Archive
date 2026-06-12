---
title: "Making PDFs Searchable Using OCR (CLI)"
date: 2014-10-06
forum: Programming Talk
---

### Post by ernz on 2014-10-06
This has taken be the entire evening to figure out. It appears that when it comes to linux, there are dozens of paid-for options or dead FOSS projects.

Lots of old tutorials reference tesseract, hocr, gs conversions, cuneiform, scantailor. I have tried many MANY combinations of all of these and they always have something wrong. Resolutions are changed, the overlaid hocr mappings are off or the font size if huge, etc. Many of the how-to's are now 8+ years old and not of any use any more.

I finally settled on [https://github.com/fritz-hh/OCRmyPDF](https://github.com/fritz-hh/OCRmyPDF)

It's a beautilfully written python extension with lots of cli flexibility. It does have lots of dependencies, but it works exceptionally well!

---

### Post by TheFu on 2014-10-07
gscan2pdf didn't work for you?
It worked on my 10.04 box, but I haven't tried it on the fresh 14.04 install.

---

