---
title: "No Entry for windows in grub"
date: 2015-12-07
forum: New to Ubuntu
---

### Post by Muhammad_GUl_ZAin_ on 2015-12-07
I am a windows 10 user and after installing ubuntu i did not get grub and computer just jumped to booting windows all the time . I started boot repair on ubuntu and then grub started appearing but now in grub i get no entry for windows . Here is my boot repair log . 
[http://paste2.org/JsbsFU5X](http://paste2.org/JsbsFU5X)
 
Ubuntu and windows are installed in two different partitions .

---

### Post by oldfred on 2015-12-07
You have UEFI hardware, and booted Boot-Repair in UEFI mode.
But both Windows & Ubuntu are installed in BIOS mode. So always boot in BIOS mode.

You should be able to just boot into Ubuntu and run this as then it will be looking for a BIOS version of Windows.

sudo update-grub

When in UEFI mode, grub will not add a BIOS entry, or when in BIOS will not add an UEFI entry to grub menu.

---

