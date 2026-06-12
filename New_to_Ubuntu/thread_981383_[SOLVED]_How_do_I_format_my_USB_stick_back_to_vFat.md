---
title: "[SOLVED] How do I format my USB stick back to vFat"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by crjackson on 2008-11-13
I was trying to use the new 8.10 tool to make a bootable usb stick for installing Ubuntu on diskless systems. It didn't work. I tried formatting to fat32 fat16 etc...

Originally it was formatted to vFat. I'm trying to restore my device to original condition. Using gparted, there doesn't seem to be an option for vFat.

How would I do this?

---

### Post by zzHanks on 2008-11-13
Try this [http://www.cyberciti.biz/faq/howto-format-usb-pen-drive](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive)

Use ```
sudo -i
``` to beccome root 
and then ```
fdisk -l
``` to find out the name of the drive

Hope this helps.

---

### Post by C.S.Cameron on 2008-11-13
Are you sure it came with VFAT? it is a Linux file system.

> The VFAT filesystem is a Linux filesystem that is compatible with Windows 95 and Windows NT long filenames on the FAT filesystem. It does not read NTFS filesystem

I just checked a brand new flash drive in gparted, it shows:
unallocated 3.94 MiB
Filesystem - fat32, Label - KINGSTON, Size - 7.47 GiB, Used - 16.00 MiB, Unused - 7.45 GiB, Flags - boot,lba

---

### Post by crjackson on 2008-11-13
> **C.S.Cameron said:**
> Are you sure it came with VFAT? it is a Linux file system.



I just checked a brand new flash drive in gparted, it shows:
unallocated 3.94 MiB
Filesystem - fat32, Label - KINGSTON, Size - 7.47 GiB, Used - 16.00 MiB, Unused - 7.45 GiB, Flags - boot,lba

Actually vfat is a supported by linux file system. Your system comes with fat32 because of the size of the pen drive. Mine is a 1 GB drive and came formated with vfat. Yes, I checked it before I changed the format.

**The fix: sudo mkfs.vfat /dev/sda1**

---

