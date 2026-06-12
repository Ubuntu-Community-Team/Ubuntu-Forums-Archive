---
title: "locking a pdf"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-07-01
Suppose i want to password protect a pdf document then how do i do it using evince.

---

### Post by brian_p on 2008-07-01
> **i.mehrzad said:**
> Suppose i want to password protect a pdf document then how do i do it using evince.

I don't think you can, evince is a viewer. mcrypt or openssl will encrypt a file but that may not be what you want.

---

### Post by Sukarn on 2008-07-01
I think acroread can do that, but I'm not sure about it.

---

### Post by gandaran on 2008-07-01
evince and acroread are only pdf readers, maybe you can do it with adobe acrobat online [http://createpdf.adobe.com/](http://createpdf.adobe.com/), haven't tried it so I don't know for sure.
what I use is pdftk, (synaptic) a command line app for manipulating pdf's, it does everything, joining, splitting and encrypt/decrypt pdf's.
there is also a gui for PDFtk [http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html).

---

### Post by brian_p on 2008-07-01
> **gandaran said:**
> what I use is pdftk, (synaptic) a command line app for manipulating pdf's, it does everything, joining, splitting and encrypt/decrypt pdf's.
there is also a gui for PDFtk [http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html).

Interesting. I've not come across pdftk before. It looks ideal for i.mehrzad use.

---

### Post by kaibob on 2008-07-01
Ghostscript can be used to password protect a PDF. The GUI for PDFtk looks much better, though.

---

