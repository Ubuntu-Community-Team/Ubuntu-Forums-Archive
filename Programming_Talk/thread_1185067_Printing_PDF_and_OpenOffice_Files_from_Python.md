---
title: "Printing PDF and OpenOffice Files from Python"
date: 2009-06-11
forum: Programming Talk
---

### Post by JoshHendo on 2009-06-11
Hi Everyone,

I am looking for a way programically to print either a PDF document or an OpenOffice (text) document.

I have had a look on Google, but unfortuantly have not been able to find much for Linux, only Windows. What I did find looks very much like what I want, but it will only work under Windows for obvious reasons (it uses win32com and Windows speficic programs).
[http://www.darkcoding.net/software/printing-word-and-pdf-files-from-python/](http://www.darkcoding.net/software/printing-word-and-pdf-files-from-python/)

Any help in this area would be great.

Thanks, Josh.

---

### Post by Zugzwang on 2009-06-12
Run in a terminal something like:

```

ps2pdf yourpdf.pdf
lpr [options] yourpdf.ps

```

Commands that are executable in the terminal can also be used from python using the subprocess module.

---

