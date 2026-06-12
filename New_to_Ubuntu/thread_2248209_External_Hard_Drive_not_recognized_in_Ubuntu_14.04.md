---
title: "External Hard Drive not recognized in Ubuntu 14.04"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by Gareth_Dowse on 2014-10-13
Hi all,

Very new to Ubuntu. Installed because I read that my external hard drive could be accessed through it as it stopped appearing in windows. I'm almost positive that it is mechanically corrupt, however I read a few suggestions on other forums and have put this into the terminal:

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x115da0f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f59da22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7831551     3915744+   7  HPFS/NTFS/exFAT

Can someone make sense of this/offer suggestions!?

Many thanks!

---

### Post by nerdtron on 2014-10-13
There are 2 drives here, a 1TB drive and 4 GB possibly usb drive. Which one is your external drive?

---

### Post by yancek on 2014-10-13
> /dev/sda1               1  1953525167   976762583+  ee  GPT

The 'ee' in your fdisk output above may be part of the problem.  ee is defined as "ee Indication that this legacy MBR is followed by an EFI header"
MBR and EFI don't mix well.  You show the 1TB drive and a 4GB windows filesystem on a flash drive.  You might get more accurate output by using GParted which should be on the Ubuntu Live CD as fdisk doesn't do well with GPT as indicated in your output.

---

### Post by ajgreeny on 2014-10-13
Just show us the output of ```
sudo parted -l
``` as suggested, though perhaps not in enough detail for you to fully understand what the error meant.

---

### Post by Gareth_Dowse on 2014-10-15
Hi all,

Thank you for the replies. I am having problems with the 1TB drive not the 4GB drive. As requested:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  316MB   315MB   fat32           EFI system partition          boot
 2      316MB   1259MB  944MB   ntfs            Basic data partition          hidden, diag
 3      1259MB  1394MB  134MB                   Microsoft reserved partition  msftres
 4      1394MB  401GB   400GB   ntfs            Basic data partition          msftdata
 5      401GB   401GB   367MB   ntfs                                          hidden, diag
 6      401GB   743GB   342GB   ntfs            Basic data partition          msftdata
 8      743GB   743GB   1049kB                                                bios_grub
 9      743GB   970GB   227GB   ext4
10      970GB   979GB   8467MB  linux-swap(v1)
 7      979GB   1000GB  21.5GB  ntfs            Basic data partition          hidden, diag


Model: USB DISK 2.0 (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4010MB  4010MB  primary  ntfs         boot

Any suggestions?

Many thanks.

---

### Post by Gareth_Dowse on 2014-10-15
> **yancek said:**
> The 'ee' in your fdisk output above may be part of the problem.  ee is defined as "ee Indication that this legacy MBR is followed by an EFI header"
MBR and EFI don't mix well.  You show the 1TB drive and a 4GB windows filesystem on a flash drive.  You might get more accurate output by using GParted which should be on the Ubuntu Live CD as fdisk doesn't do well with GPT as indicated in your output.

Can you walk me through this step by step? I really have no idea what I'm doing. Assume I know nothing!

---

### Post by irv on 2014-10-15
Boot with live DVD or USB. Search for gparted open gparted and look for your drive.
[ATTACH=CONFIG]257225[/ATTACH][ATTACH=CONFIG]257226[/ATTACH]

---

### Post by Gareth_Dowse on 2014-10-15
Ok I have used gparted and have the attached screenshots: [ATTACH=CONFIG]257228[/ATTACH][ATTACH=CONFIG]257229[/ATTACH]

When I tried to 'recover data' under device, this error message came up.

What do I do from here?

Many thanks.

---

### Post by irv on 2014-10-15
Your screen shot of gparted is showing your main hard drive sda, look for sdb. you don't want to change anything on sda. Once you find sdb post another screen shot.

EDIT, your error message was that you type gpart and not gparted. and it couldn't fine it.

---

### Post by yancek on 2014-10-15
The output you posted in your post #5 above shows that you have a separate EFI partitiion so that you can boot GPT/EFI with both windows and Ubuntu.  It also shows a separate bios_grub partition.    These two conflict.  You need to use UEFI/GPT or MBR so you need to change one.  I don't use UEFI so can't tell you how to do that but from what I have read hear you might be able to do it with the boot-repair software.  This is the 1TB drive which appears to have both a windows installation and Ubuntu.

---

### Post by irv on 2014-10-15
By the way Windows will not be able to read sda9 but Linux will read all the partitions. That why you see them in gparted.

---

