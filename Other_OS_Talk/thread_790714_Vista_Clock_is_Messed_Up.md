---
title: "Vista Clock is Messed Up"
date: 2008-05-11
forum: Other OS Talk
---

### Post by SIXAXIS on 2008-05-11
My laptop is dual-booting Ubuntu 8.04 and Vista. Everytime I go from Ubuntu to Vista, the clock in Vista goes ahead by 4 hours. I have to manually change it back. Is there a way that I can stop Ubuntu from changing the clock, or to make sure that Vista's clock stays at the right time?

---

### Post by aamukahvi on 2008-05-11
[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html#s-tzconfig](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html#s-tzconfig)

refer to 16.1, long story short:
set utc to no in /etc/default/rcS

---

### Post by chris4585 on 2008-05-11
> **aamukahvi said:**
> [http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html#s-tzconfig](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html#s-tzconfig)

refer to 16.1, long story short:
set utc to no in /etc/default/rcS

This was **VERY** annoying in vista when I used vista... every week, literally (YES every week) I had to reset the stupid clock.

---

