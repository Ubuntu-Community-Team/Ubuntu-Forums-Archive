---
title: "eager to learn to extract ascii from pdf using pstotxt via ghostscript"
date: 2015-09-19
forum: New to Ubuntu
---

### Post by Andy_Climer on 2015-09-19
I'm currently under the impression that the only for me to extract ASCII from PDF is by using pstotext and ghostscript. conceptually, I - might - understand. I just do not know how to put into practice via terminal. I'm trying to make PDF, scanned, physical-books more legible on my Nook Gen 1 that i picked up from a friend. As far as I am aware, the only way to go about this is to extract the ASCII text from the original PDF. 

Please teach me. 
I am a aspiring, newb, Ubuntu 14.04 user who just wants to learn the way of the force.

---

### Post by TheFu on 2015-09-19
scanned pdf files don't work with pdftotext because images are't text.
You'll need to use some OCR for any hope of that working - just be aware that OCR is'nt all that good.  Take a look at **gscan2pdf** - it is a scanner + OCR + PDF maker. [http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html](http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html)

---

### Post by Andy_Climer on 2015-09-20
Just to be sure,do you mean pstotext?  this... [http://manpages.ubuntu.com/manpages/lucid/man1/pstotext.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/pstotext.1.html)

I will give your suggestion a shot either way, for learning's sake. I appreciate your input.

---

### Post by TheFu on 2015-09-20
No.  pdftotext is the tool to convert pdf -to- text.  PDF is highly related to PS, but if you don't have a PS file and do have a PDF file, then using pdftotext is the correct choice.

---

