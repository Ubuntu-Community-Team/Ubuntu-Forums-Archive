---
title: "[SOLVED] need help with error message ..."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-04
I installed libdvdcss2_1.2.9-1_i386.deb so I could play DVD's.
Always worked in the past. today I did a new Ubuntu 7.10 install
and after installing libdvdcss2_1.2.9-1_i386.deb I received the 
following error while trying to install some stuff (including an
update for libdvdcss2 ...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how do I correct this (I don't know how to run dpkg manually. Thanks

---

### Post by Maestro23 on 2008-06-04
Run the command listed in a terminal:

> sudo dpkg --configure -a

Let us know what happens.

---

