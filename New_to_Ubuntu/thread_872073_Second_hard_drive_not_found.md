---
title: "Second hard drive not found"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by quantum_mechanik on 2008-07-27
Second hard drive not found
Hi. I'm completely 100% new to uBuntu, and I've a bit of a problem.

I installed it on my Acer Aspire 9410, as a dual-boot thing, and now I can't find my second hard drive--the one with all my media on it. Is there any way to search for it? It's the e:\

---

### Post by silkstone on 2008-07-27
It won't show as a drive letter (Linux doesn't use drive letters) but try clicking on Places > Home Folder and see if the drive appears in the list down the left hand side. It will be called by a name but it should be obvious if it's there.

Click on that name to mount it - you may be asked for your password. You can tell Ubuntu to remember this password, or you can edit a file so the drive mounts at boot - please ask for instructions on this, but first see if it's there.

---

### Post by quantum_mechanik on 2008-07-27
> **silkstone said:**
> It won't show as a drive letter (Linux doesn't use drive letters) but try clicking on Places > Home Folder and see if the drive appears in the list down the left hand side. It will be called by a name but it should be obvious if it's there.

Click on that name to mount it - you may be asked for your password. You can tell Ubuntu to remember this password, or you can edit a file so the drive mounts at boot - please ask for instructions on this, but first see if it's there.

It doesn't. I've got Home Folder, File System, Audio CD and 1.0 GB Media. No hard drives that I can see! I click computer, and the C: shows up (under ACER) but no e:.

---

### Post by perce on 2008-07-27
is it an external hard drive?

---

### Post by quantum_mechanik on 2008-07-27
Nope. It's inside.

---

### Post by halitech on 2008-07-27
what format was it? ie. NTFS, FAT32, FAT16?

can you open a terminal and post the output of

```
sudo fdisk -l
```  (thats a lowercase L, not the number 1)

---

### Post by quantum_mechanik on 2008-07-27
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdfbbdfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  27  Unknown
/dev/sda2   *        1021        7807    54516577+   7  HPFS/NTFS
/dev/sda3            7808       14593    54508545    7  HPFS/NTFS

Disk /dev/mmcblk0: 1021 MB, 1021313024 bytes
15 heads, 46 sectors/track, 2890 cylinders
Units = cylinders of 690 * 512 = 353280 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        2891      997252+   6  FAT16

---

### Post by halitech on 2008-07-27
looks to me that all the computer is seeing is your primary master (/dev/sda) and what looks to me like a usb thumbdrive (/dev/mmcblk0)

have you checked your BIOS to make sure the computer is seeing the drive?

edit: actually, looking at the 1 hard drive, it is showing it is NTFS formatting, did you use WUBI to install?

---

### Post by quantum_mechanik on 2008-07-27
> **halitech said:**
> looks to me that all the computer is seeing is your primary master (/dev/sda) and what looks to me like a usb thumbdrive (/dev/mmcblk0)

have you checked your BIOS to make sure the computer is seeing the drive?

You are giving me far too much credit. A) How do I do that, and B) It shows up in Windows Vista as E:\, but it might be partitioned. I'm only somehat sure what that word means, by the way.

---

### Post by halitech on 2008-07-27
usually when booting the computer, you should get an option to Press F10 or Del to enter the BIOS and in there you should see a section on hard drives (might be basic info)

when it comes to Vista I'm lost as I don't use it but in the control panel, there should be a section on Admin controls, see if there is anything about dsk management and see if it shows as a single drive (almost thinking it is) or multiple drives.

---

### Post by fraser-08 on 2008-07-27
> **halitech said:**
> usually when booting the computer, you should get an option to Press F10 or Del to enter the BIOS and in there you should see a section on hard drives (might be basic info)

when it comes to Vista I'm lost as I don't use it but in the control panel, there should be a section on Admin controls, see if there is anything about dsk management and see if it shows as a single drive (almost thinking it is) or multiple drives.

Right click My computer, then click Manage  :P:P




Fraser

---

### Post by halitech on 2008-07-27
that works for me :)

---

