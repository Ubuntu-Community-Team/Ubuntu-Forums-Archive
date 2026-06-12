---
title: "How do i resize my ubuntu partition?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by timotheetc on 2012-06-08
I installed ubuntu 12.04 using the windows installer. I soon realized the 10 GB size i chose on installation was not enough as i tryed to install a game (Ryzom) and was told i didn't have enough space. I tried Gparted, but couldnt resize as the windows partion i wanted to shrink was mounted and it didnt show the ubuntu partition for mto increase ( i'm very new to this so may be missing something obvious).

Could someone explin how to achieve this,if it's possible?

Thanks in advance

Timothee

---

### Post by wilee-nilee on 2012-06-08
[COLOR=White].[/COLOR]

---

### Post by coffeecat on 2012-06-08
> **timotheetc said:**
> I installed ubuntu 12.04 using the windows installer.

This sounds as though you ran the wubi.exe installer from inside Windows, which would mean that you have a wubi installation, not a conventional Ubuntu installation on its own partition. The reason Gparted cannot resize a wubi installation is that wubi Ubuntu is installed in a virtual partition in the file root.disk inside your Windows partition.

See this guide to wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Section on resizing the wubi virtual disk:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

Which links to this guide:

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by mbzn01 on 2012-06-08
Not sure with wubi, but try booting the live cd or go into ubuntu use a program called 'startup disk creator' with an USB flash drive and copy the ISO to a bootable medium. Boot from that and you won't have the mounted problem. Hope that helps.

---

### Post by wilee-nilee on 2012-06-08
> **mbzn01 said:**
> Not sure with wubi, but try booting the live cd or go into ubuntu use a program called 'startup disk creator' with an USB flash drive and copy the ISO to a bootable medium. Boot from that and you won't have the mounted problem. Hope that helps.

Wubi is a file in widows not a partition.

---

