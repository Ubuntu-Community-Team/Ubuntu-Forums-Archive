---
title: "Printer/scanner problem"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by neboparker on 2008-11-04
I have just swapped from windows to Ubuntu and finding my way round at the moment, the only snag I have found is with my printer, it's an all in one, the printer & fax work fine but I'm struggling to get the scanner up and working, anyone have any tips or ideas I might try?

---

### Post by superprash2003 on 2008-11-04
have you tried going to GIMP and trying out file->acquire->xsane ?

---

### Post by neboparker on 2008-11-04
Yep I have done that and no luck

---

### Post by JohnnyVW on 2008-11-04
What brand and model is the all-in-one?

---

### Post by neboparker on 2008-11-04
It is a HP officejet j5780
However I try and access the scanner I just get 'failed to open device'

---

### Post by JohnnyVW on 2008-11-04
> **neboparker said:**
> It is a HP officejet j5780
However I try and access the scanner I just get 'failed to open device'

Go here:  [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

hplip was a savior for me with my HP Photosmart c6280 AIO.  According to the hplip site, your J5780 is supported.

Just download the program and follow the instructions to install it.

I use my scanner daily with gscan2pdf for work.

---

### Post by philinux on 2008-11-04
Hplip is installed by default.

---

### Post by JohnnyVW on 2008-11-04
> **philinux said:**
> Hplip is installed by default.

But, the new version from hplip supports way more AIO's.  I had this same issue with my C6280.  It didn't work right (only printed) with the default version.

---

