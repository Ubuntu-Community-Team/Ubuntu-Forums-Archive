---
title: "Windows 7 Partition Guide"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by ClarkH85 on 2013-04-18
Does anyone have a link to a guide for creating a partition and installing Windows 7 on my machine? I can find a ton of guides which involve creating a partition for a Linux OS assuming Windows 7 is installed first, but am having trouble finding a guide for a machine that only currently has Ubuntu installed.

Thanks!

---

### Post by fantab on 2013-04-18
You can use gparted to create a NTFS partition(s) or just 'unallocated space". Then use the Windows Installer to reformat the partitions to NTFS or create NTFS partitoins. Then install Windows.

Install Windows to the PRIMARY PARTITION ONLY. (If you use MBR partition Table then you can only have Four Primary Partiions).

You will have to repair or fix Grub after installing Windows. You can search this forum there is plenty of info on how to do it. Or use [BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair").

---

