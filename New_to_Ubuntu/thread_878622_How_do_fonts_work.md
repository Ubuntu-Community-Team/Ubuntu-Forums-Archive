---
title: "How do fonts work?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by klas_katt on 2008-08-03
[SOLVED]How do fonts work?
There are a multitude of "fonts" in OpenOffice and I don't want them there! (AlMateen Rasheeq) I want the likes of new century schoolbook, helvetica or bodoni. I DON'T mean character encodings or l10n or i18n. I do not want cyrillic, farsi, hebrew or hangul. How do I install new fonts and what packages contain useful fonts? I need a guide through the debconf hassle.

---

### Post by northern lights on 2008-08-03
Run ```
sudo apt-get install msttcorefonts
```This package contains most Microsoft TrueType fonts such as Arial, Verdana, Helvetica, MS Sans Serif, etc.

The fonts are located in "/usr/share/fonts/truetype". Delete from there, if you want to delete single fonts (from Synaptic you can only delete several at a time). Run ```
sudo fc-cache -fv
```afterwards.

---

### Post by klas_katt on 2008-08-03
"Configuring msttcorefonts 

msttcorefonts uses defoma
Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts. The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf. For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required.
 <Ok>"

---

### Post by billgoldberg on 2008-08-03
You can always download fonts from the internet and put them in the home folder.

Create a folder called 

.fonts

(don't forget the ".")

And put them there.

.fonts will be a hidden folder, press "ctrl +h" to view hidden folders.

All programs will have access to them.

---

### Post by klas_katt on 2008-08-03
Thank you!
No format restrictions?

---

### Post by klas_katt on 2008-11-18
Can I get rid of the "participants" fonts. They are many and not very useful. How does one know which package a particular font belongs to?

---

