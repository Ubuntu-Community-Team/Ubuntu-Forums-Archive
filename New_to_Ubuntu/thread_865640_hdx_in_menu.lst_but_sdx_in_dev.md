---
title: "hdx in menu.lst but sdx in dev"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Whydoe on 2008-07-20
I'm a bit confused as to why my hard drives are recognized by hd0,0, etc in menu.lst and are referred to sda, sdb, etc in dev.  I'm only concerned because I plan on cloning my linux partition onto another hard drive with the "dd" command soon.

---

### Post by phidia on 2008-07-20
Grub uses the hdx,y notation to ID devices. You will also see the /dev/sdx identification in menu.lst too, but the grub commandline only recognizes hdx,y.
I hope that clears up an unclear situation-it is a little confusing.

---

