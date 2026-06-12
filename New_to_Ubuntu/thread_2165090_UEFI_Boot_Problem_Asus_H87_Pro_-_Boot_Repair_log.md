---
title: "UEFI Boot Problem Asus H87 Pro - Boot Repair log"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by sandipan2 on 2013-08-03
Hi,

I just got a new system with the following config

ASUS H87-PRO - ATX / H87 
Intel Core i5-4430 
Kingston 8GB DDR3 PC10600 1333MHz (2x4GB) 
2 x WD Red 3TB SATA III

Tried to install Ubuntu 13.04 and it went through successfully but I am not getting the Grub menu. Tried reinstalling with the instructions from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but still the same problem. Ran boot repair with "recommended repair" option successfully  but still do not get the boot menu and my Mobo shows the Bios.

The Boot-Repair log is here [http://paste.ubuntu.com/5943315/](http://paste.ubuntu.com/5943315/)

Just to be sure that there is no problem with the Mobo I installed windows which went through successfully. Can someone help please I really do not want to have windows on this system.

---

### Post by Vladlenin5000 on 2013-08-03
Are you using the EFI method in order to be able to dual-boot a previously installed Windows or just Ubuntu? If the latter then it might be better to try the legacy mode.

---

### Post by sandipan2 on 2013-08-03
Thanks! Just used legacy mode with EFI and it now works like a charm. How do I mark this as solved?

---

