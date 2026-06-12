---
title: "Finding multicols.sty: Latex, TexLive and Lyx/Kile"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by filde on 2012-09-03
Kiaora,

Just made the switch from Windows to Ubuntu and what a wonderful move it is. Only had a few issues, one I can't seem to resolve. 

I have installed Lyx (and Kile) and need to use the multicols package. Every time I specify in the preamble however, Lyx cannot find the .sty. I have run ```
$sudo apt-get install texlive-full
``` and made the gigabyte download. 

Other packages such as 'subfig' and 'graphicx' seem to work OK.  

Does anyone have any hints? Do I need to install the packages from the TexLive directory similar to MikTex?

Regards,
Phil Donovan

---

### Post by gauavp on 2012-09-03
> **filde said:**
> Kiaora,

Just made the switch from Windows to Ubuntu and what a wonderful move it is. Only had a few issues, one I can't seem to resolve. 

I have installed Lyx (and Kile) and need to use the multicols package. Every time I specify in the preamble however, Lyx cannot find the .sty. I have run ```
$sudo apt-get install texlive-full
``` and made the gigabyte download. 

Other packages such as 'subfig' and 'graphicx' seem to work OK.  

Does anyone have any hints? Do I need to install the packages from the TexLive directory similar to MikTex?

Regards,
Phil Donovan
You can use tlmgr for installing new packages. for help please visit [http://tug.org/texlive/doc/tlmgr.html](http://tug.org/texlive/doc/tlmgr.html)

---

