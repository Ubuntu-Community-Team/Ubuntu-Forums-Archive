---
title: "[SOLVED] Tesseract problem"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-10-12
I am using Ubuntu 8.10. I have gone into Synaptic Package Manager and in Graphics (universe) installed tesseract-ocr (2.03-2) and tesseract-eng (2.00.1) as well as tesseract for several other languages. I have then gone to Terminal and given it the following command (after some advice from kwacka):
  
tesseract test10.tif test10 -l eng 

I got these results: 

> george@george-desktop:~$ tesseract test10.tif test10 -l eng
Tesseract Open Source OCR Engine
TIFFOpen: test10.tif: Cannot open.
tesseract:Error:Read of file failed:test10.tif
Signal_exit 31 ABORT. LocCode: 3 AbortCode: 3
george@george-desktop:~$ 


This test file is from a photocopied page of an old book. The print, although quite readable to the naked eye, is in an italicized font and is less than perfect. Is the problem simply that Tesseract cannot read the text? If that is not the problem, what is?

---

### Post by Patb on 2008-10-12
Ludwig, I think you will need to save the tif file as an uncompressed file.  When you use Gimp or Xnview to convert the .pnm file (from your other thread), try selecting no compression. 

Cheers, Pat.

---

### Post by Ludwig9 on 2008-10-13
> **Patb said:**
> Ludwig, I think you will need to save the tif file as an uncompressed file.  When you use Gimp or Xnview to convert the .pnm file (from your other thread), try selecting no compression. 

Cheers, Pat.
I had saved it without compression. In any case, I made a new test page and Tesseract worked with it, not perfectly but well enough, much better than I had gotten from gocr in XSANE. Thanks, Patb.

---

