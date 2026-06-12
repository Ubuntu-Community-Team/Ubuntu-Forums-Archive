---
title: "&quot;Unallocated&quot; USB"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Matias_ on 2014-03-08
I tried to make a WinXP booteable flash drive on a Virtual Machine with said OS, it didn't work and the drive was unrecognized by ubuntu so I tried to format it on the Virtual Windows XP with a FAT32 file system, when it finished i rebooted my netbook but my pen drive was still unrecognized by ubuntu, it kept working on the Virtual Machine though. On Gparted, /dev/sdb shows a partition with both name and file system defined as "unallocated" , only it's size as 7,45GB with no Used, Unsused valors or Flags.
Sorry for any kind of errors, english is not my mother language.

---

### Post by phidia on 2014-03-08
In Ubuntu open a terminal with the drive inserted and issue > fdisk -l. Copy/paste the output from that.

---

### Post by ajgreeny on 2014-03-08
What do you want to do with the drive now?

If you don't want anything that is now on the USB, and it sounds as if there is nothing on it anyway, I suggest you use gparted again and go to **Device -> Create new partition table** and make a new default table, then a new partition of whatever filesystem you want, eg fat32 for a USB.

---

