---
title: "Headers not found"
date: 2007-06-04
forum: Programming Talk
---

### Post by Seplinux on 2007-06-04
I'm trying to compile a program with #includes, and the compiler give me :

hellocurrent.c:1:24: error: linux/init.h: No such file or directory
hellocurrent.c:2:26: error: linux/module.h: No such file or directory
hellocurrent.c:4:25: error: asm/current.h: No such file or directory
hellocurrent.c:5:18: error: list.h: No such file or directory

I have located the files, they are on their directories :

/usr/src/linux-headers-2.6.20-16/include/linux/module.h
.....etc..


I have done :
sudo apt-get install build-essential
sudo aptitude install build-essential
sudo updatedb
....
 and no success

Anybody know which could be my problem. Thas has been after update Ubuntu to 7.04

Thanks in advance

---

### Post by FuturePast on 2007-06-04
What's your compiler command line? Does it contain [FONT="Courier New"]**[SIZE="3"]-I[/SIZE]**[/FONT]?

---

### Post by Seplinux on 2007-06-05
Thank you futures past, I finally fix the problem re-installing the gcc.

---

