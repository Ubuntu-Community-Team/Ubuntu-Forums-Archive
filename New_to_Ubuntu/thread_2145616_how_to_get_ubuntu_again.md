---
title: "how to get ubuntu again?"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by ananthuvas on 2013-05-16
hi friends i have install ubuntu 12.04 and windows7 in my system.
when i start pc it will direct me to the list where i can select
1.ubuntu
2.windows7
recently i have install windows 8 but im not getting the chance to select ubuntu
now there is only 
1.windows7
2.windows8
i want to get back ubuntu without re installing it!
please help me!

---

### Post by papibe on 2013-05-16
Hi ananthuvas. Welcome to the forum ):P

It seems that the Windows8 installer rewrite the MBR block, effectively removing grub.

Using the Ubuntu installation CD/USB as a live media, and the program Boot-Repair, you can reinstall it, and put all 3 on the boot list. Here's a [tutorial]("https://help.ubuntu.com/community/Boot-Repair") on how to do it.

Let us know how it goes.
Regards.

---

### Post by Reggy on 2013-05-16
Before doing boot-repair, verify that the partition that contained Ubuntu is still intact, and that it was not overwritten during Windows installation.

---

### Post by ananthuvas on 2013-05-16
thank you very much for quick reply i will do it and let u know

---

