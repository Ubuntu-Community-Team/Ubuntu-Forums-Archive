---
title: "[SOLVED] xetex in Intrepid doesn't work"
date: 2008-12-06
forum: Programming Talk
---

### Post by mmand on 2008-12-06
Sorry if this has been posted before, the internal search function only lets me search once every 15 seconds (and I'm a very impatient person) and Google hasn't given me any help tonight.

After installing texlive-full (and all 1.1 GB of required packages...0.0), and trying to run pdflatex on a xetex-written document, I get the following error:

```

 ********************************************
 * XeTeX is required to compile this document.
 * Sorry!
 ********************************************

```Funny...texlive-xetex is an included package in texlive-full, and removing and reinstalling texlive-xetex didn't make a bit of difference.

Does anyone have any suggestions? I've had nothing but problems with Intrepid and I'm so very tempted to move back to Hardy, but I've FINALLY been able to get true DUAL-monitors working, and am hesitant to lose it again.

Thanks in advance.

---

### Post by hugmenot on 2008-12-06
Easy, the command to process a Xelatex document is not pdflatex but xelatex.
Try it.

---

### Post by mmand on 2008-12-06
Thanks. It would be nice if pdflatex were able to do this (or give me better error messages), but oh well.

---

### Post by hugmenot on 2008-12-06
Why? Xetex is an alternative tex engine to pdftex. Both output to PDF as the native format but they use very different approaches.

---

