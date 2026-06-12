---
title: "Me-TV in 11.10 Oneiric not woking"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SirPecanGum on 2011-10-01
I installed Me-TV from the Ubuntu Software Center but it fails to run giving error:

me-tv: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory


Needless to say I have tried installing the missing file(s) as they appear through the above method and by compiling from source (me-tv_1.3.6.orig.tar.gz) but it does not work. Any idea what I'm doing wrong? BTW, it works fine in Fedora 15...

---

### Post by P-I H on 2011-10-01
I am using MeTV on Oneiric, at least since Beta1, without problem.
It's a fully updated AMD64 installation with Nvidia graphics.
I installed with Software Center.
libgtkmm-3.0-1, version 3.2.0-0ubutu1, and libgtkmm-2.4-1c2a, version 1:2.24.2-1, are installed.

---

### Post by SirPecanGum on 2011-10-01
Thanks for your feedback. I gave up and reinstalled 11.10 and Me-TV is working perfectly now. The only other thing that occurs to me is that the 11.10 installer crashed before completion. I was able to boot and once updated assumed all was well but perhaps not... 

This install completed fine, the only difference was not updating while installing - an error that occurred with me on 10.04 as well.

---

