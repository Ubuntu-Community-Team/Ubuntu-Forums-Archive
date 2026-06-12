---
title: "how to access 2nd drive"
date: 2021-03-20
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2021-03-20
i have 1 drive with ubuntu. Properties are Device/dev/sdb1,uuid 634-f955,
partition type-efi system, fat 32 bit  version- mounted at/boot/efi. The 2nd one listed as /dev/sba, mounted at boot/efi.
So can someone help with how to access second drive? Thx

---

### Post by tea for one on 2021-03-20
Any reason that you cannot use the file manager?

Files > Other Locations

---

### Post by deadflowr on 2021-03-20
Are you saying one is mounted at /boot/efi and the other is mounted at boot/efi?

---

### Post by Impavidus on 2021-03-20
sdb1 is not a drive, it's a partition, which is part of a drive. It's the first partition of the second drive. sda is a drive, the first drive.

Partitions that get mounted at /boot/efi are rather special. They have a very specific purpose at boot time, telling the computer where it can find a bootloader, which will in turn, in several stages, load an operating system. You don't use an efi partition for anything else.

---

### Post by rsteinmetz70112 on 2021-03-20
Open a terminal and enter:

```
$lsblk
```

That will list all of the existing block devices and their current mount points
Copy and Paste the results in a response - use code tags. [COSE] [/CODE] or highlight the code and press the # button on the advanced editor.
You apparently have two hard drives - /dev/sda and /dev/sdb but the mount points don't make sense to me.

---

### Post by grahammechanical on 2021-03-20
Are you able to load Ubuntu? Does sda contain Microsoft Windows? Are you asking how to access the Windows drive from Ubuntu? If you have Windows is Fast Startup turned off. It is a form of hibernation and I do not think that a Linux file manager can read a Windows drive/partition when Windows is hibernated.

Regards

---

### Post by yancek on 2021-03-20
The first partition you mention, sdb1 is in all likelihood an efi partition on that disk.  There is no sba, read and spellcheck before posting.  The second one, sba should refers to the drive and should have a number after it.  You may have an EFI partition on both hard drives but no one will be able to tell unless you post the output of the command suggested above or the output of:  sudo fdisk -l OR sudo parted -l (Lower case Letter L in both commans).

---

### Post by tuesdaybarrett on 2021-03-21
the ssd is blank. [COLOR=#000000]sudo fdisk -l is listed below[/COLOR]
```
Disk /dev/loop0: 98.35 MiB, 103129088 bytes, 201424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 99.21 MiB, 104026112 bytes, 203176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 61.63 MiB, 64626688 bytes, 126224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 64.35 MiB, 67477504 bytes, 131792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 161.41 MiB, 169254912 bytes, 330576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 218.99 MiB, 229629952 bytes, 448496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 61.59 MiB, 64585728 bytes, 126144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 55.46 MiB, 58159104 bytes, 113592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: SanDisk SD6SB1M1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EZEX-60Z
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9A7982C6-04CE-479B-BF4E-22CB9A2317AF


Device       Start        End    Sectors  Size Type
/dev/sdb1     2048    1050623    1048576  512M EFI System
/dev/sdb2  1050624 1953523711 1952473088  931G Linux filesystem




Disk /dev/loop8: 64.77 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 51.02 MiB, 53501952 bytes, 104496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 32.28 MiB, 33845248 bytes, 66104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 229.41 MiB, 240558080 bytes, 469840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 272.11 MiB, 285327360 bytes, 557280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 172.06 MiB, 180420608 bytes, 352384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 21.18 MiB, 22212608 bytes, 43384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 21.26 MiB, 22290432 bytes, 43536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop17: 272.12 MiB, 285339648 bytes, 557304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop18: 9.07 MiB, 9510912 bytes, 18576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop19: 148.82 MiB, 156045312 bytes, 304776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop20: 174.56 MiB, 183037952 bytes, 357496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop21: 75.95 MiB, 79642624 bytes, 155552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop22: 19.61 MiB, 20561920 bytes, 40160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop23: 51.04 MiB, 53522432 bytes, 104536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop24: 6.68 MiB, 7004160 bytes, 13680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop25: 235.96 MiB, 247422976 bytes, 483248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop26: 32.97 MiB, 34570240 bytes, 67520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop27: 229.54 MiB, 240689152 bytes, 470096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop28: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop29: 148.82 MiB, 156049408 bytes, 304784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop30: 55.38 MiB, 58073088 bytes, 113424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop31: 162.87 MiB, 170778624 bytes, 333552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop32: 31.09 MiB, 32595968 bytes, 63664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop33: 19.61 MiB, 20561920 bytes, 40160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop34: 217.89 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
here is parted -l output
```
Error: /dev/sda: unrecognised disk label
Model: ATA SanDisk SD6SB1M1 (scsi)                                        
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4

```
does this help in solving problem.thx for help

---

### Post by tea for one on 2021-03-21
I assume that your [COLOR="#0000FF"]2nd drive[/COLOR] is the Sandisk device with **unknown partition table**?

In order to access it, you will need to create a partition table and a partition.

Gparted or gnome-disk-utility will do this.

---

### Post by tuesdaybarrett on 2021-03-21
thx

---

