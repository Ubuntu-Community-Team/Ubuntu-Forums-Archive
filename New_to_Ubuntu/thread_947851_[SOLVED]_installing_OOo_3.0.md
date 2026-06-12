---
title: "[SOLVED] installing OOo 3.0"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by T2manner on 2008-10-14
I downloaded the big tar.gz file yesterday for openoffice.org 3.0
it came with a folder full of tons of deb files.
i'm not sure how to install it though.
idk if i have to install each one of the deb files or what.

---

### Post by LowSky on 2008-10-14
very simple first in synaptic remove openoffice 2
then follow these instructions

open terminal
```
cd */insert/path/to/debs*
sudo dpkg -i *.deb
```
then after thats done then do this
```
cd */insert/path/of that folder/thats/in/deb/folder/*
sudo dpkg -i *.deb
```

should be done, hopefully you understand what I wrote

---

### Post by T2manner on 2008-10-14
yeah
i'll try that.

EDIT:
There isn't another folder in the DEBS folder.

EDIT2:
I had to install the desktop-integration thing.

---

