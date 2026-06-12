---
title: "advanced gparted help for ubuntu 20.04"
date: 2020-12-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-12
error

---

### Post by rburkartjo on 2020-12-12
this is the right screenshot
when i was installing ubuntu 20.04 i some how left a fat/32/ef partition on /dev/sda1 which is set as boot..i want to delete this and increase/dev/sda5 and change the flag as boot/tks

---

### Post by oldfred on 2020-12-12
You do not say what your issue is?
Little key icons mean you are using gparted with mounted partitions which then cannot be changed.
You have to use gparted from Ubuntu live installer or a gparted live flash drive.

I wish Ubuntu would not let you install with MBR(msdos) partitions.
UEFI strongly suggests gpt(GUID), Windows requires gpt, and Ubuntu normally uses gpt unless you manually partition in advance with MBR.I have only used gpt for new or repartitioned drives since 2010. Back then it was BIOS only, but now UEFI systems.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

If you use gparted to convert drive to gpt, it will erase drive & you have to totally reinstall.
You may be able to convert, but still have to reinstall grub in UEFI boot mode.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by rburkartjo on 2020-12-12
tks fred
just cant believe that i had the old boot partition in. thought i had ubuntu install to select whole hard drive.

---

### Post by CelticWarrior on 2020-12-12
> **rburkartjo said:**
> thought i had ubuntu install to select whole hard drive.

In UEFI mode and using the whole drive it'll always create a the ESP and root.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

