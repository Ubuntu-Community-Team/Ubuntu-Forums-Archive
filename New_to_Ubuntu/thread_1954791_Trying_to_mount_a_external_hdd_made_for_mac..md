---
title: "Trying to mount a external hdd made for mac."
date: 2012-04-08
forum: New to Ubuntu
---

### Post by super mushroom on 2012-04-08
This is the error i get when mounting: **Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2**

and i don't know how to change the file system type. 
when i do  sudo fdisk /dev/sdb2 and enter p no partitions show up?

---

### Post by roelforg on 2012-04-08
run:
```

sudo fdisk -l

```

---

### Post by coffeecat on 2012-04-08
> **super mushroom said:**
> This is the error i get when mounting: **Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2**

How are you trying to mount it? If from the terminal, what command?

> **super mushroom said:**
> and i don't know how to change the file system type. 

Please explain. Do you mean change the filesystem type in your command?

> **super mushroom said:**
> when i do  sudo fdisk /dev/sdb2 and enter p no partitions show up?

If your external HDD was formatted in MacOS, then it is almost certainly formatted HFS+ and will most likely have a GUID partition table (GPT). fdisk does not support gpt - you usually get a message saying so. Instead, run:

```
sudo parted -l
```

You may need to install parted.

---

### Post by roelforg on 2012-04-08
> **coffeecat said:**
> How are you trying to mount it? If from the terminal, what command?



Please explain. Do you mean change the filesystem type in your command?



If your external HDD was formatted in MacOS, then it is almost certainly formatted HFS+ and will most likely have a GUID partition table (GPT). fdisk does not support gpt - you usually get a message saying so. Instead, run:

```
sudo parted -l
```

You may need to install parted.

lol,
both posting essentially the same thing with a different prog.

Also, i think he's missing the fs from the collection, like when it gives these errors until you update the fs-tools from the fs.

---

### Post by coffeecat on 2012-04-08
> **roelforg said:**
> 
Also, i think he's missing the fs from the collection, like when it gives these errors until you update the fs-tools from the fs.

I'm *hoping* part of the problem is fdisk itself. 2GB pendrive with GPT and FAT32 partition (just as a test). Compare these outputs:

```
sudo fdisk -l
-
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     4030463     2015231+  ee  GPT
```

```
sudo parted -l
-
Model:  USB DISK 2.0 (scsi)
Disk /dev/sdc: 2064MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2063MB  2062MB  fat32
```

Fdisk won't show us the filesystem type if the OP has a GPT. Let's see anyway.

[quote="super mushroom"]
when i do sudo fdisk /dev/sdb2 and enter p no partitions show up? [/quote]

That's right. If you have a GPT, nothing shows up in fdisk if you do that. Or you will get something similar to the above if you do "sudo fdisk -l". Try with parted.

---

### Post by super mushroom on 2012-04-08
@coffiecat 

well I tryed mounting it by using mount and it didn't work but when I got that error I posted I mounted byrightclicking in the files window and pressing mount. 

im trying to change the file system type of the hdd because it doesn't work in Linux (i'm guessing b/c its made for mac.
And I don't know if it was formatted in MacOS, because I just bought it hoping I could make it work in Linux Ubuntu

What I got from:sudo fdisk -l
```

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c185c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   127928319    63860736   83  Linux
/dev/sda3       127930366   312580095    92324865    5  Extended
/dev/sda5       127930368   304265215    88167424   83  Linux
/dev/sda6       304267264   312580095     4156416   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4256 MB, 4256169984 bytes
255 heads, 63 sectors/track, 517 cylinders, total 8312832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0fb6078

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```and sudo parted -l
```

sudo parted -l
Model: ATA WDC WD1600BEVT-7 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   65.5GB  65.4GB  primary   ntfs
 3      65.5GB  160GB   94.5GB  extended
 5      65.5GB  156GB   90.3GB  logical   ext4
 6      156GB   160GB   4256MB  logical


Backtrace has 12 calls on stack:
  12: /lib/libparted.so.0(ped_assert+0x2e) [0x7f3efcdf839e]
  11: /lib/libparted.so.0(ped_geometry_read+0x80) [0x7f3efcdff8e0]
  10: /lib/libparted.so.0(hfsplus_probe+0x238) [0x7f3efce1cfa8]
  9: /lib/libparted.so.0(ped_file_system_probe_specific+0x53) [0x7f3efcdf9853]
  8: /lib/libparted.so.0(ped_file_system_probe+0x52) [0x7f3efcdf9932]
  7: /lib/libparted.so.0(+0x43fb5) [0x7f3efce2cfb5]
  6: /lib/libparted.so.0(ped_disk_new+0x58) [0x7f3efcdfe588]
  5: parted() [0x406cb1]
  4: parted() [0x407a7a]
  3: parted(main+0x1483) [0x406403]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f3efc60030d]
  1: parted() [0x406451]

```

---

### Post by coffeecat on 2012-04-09
> **super mushroom said:**
> 
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

That output from fdisk says that there is no valid partition table. Had there been a GUID partition table you would have seen the "WARNING: GPT (GUID Partition Table) detected" message I posted from the output for my pendrive. Which is interesting, because if there is no partition table it shouldn't work with a Mac either.

Also - there is no output at all for sdb from parted. Did you have the drive plugged in when you ran parted, and did you post all the output? If there really is no partition table on the 500GB drive, then you would have seen the message "Error: /dev/sdb: unrecognised disk label" from parted.

Before we go any further, what exactly is this external HDD made for a Mac? Is it one that came pre-formatted for a Mac, or one that has been formatted in MacOS? Is it brand-new or have you used it before? Make, model? The reason I ask is that it is probably easy to create a partition table and reformat it (if there is no data on it you want to save) with Gparted, but we need to make sure that it is not some unusual device that will present problems.

---

### Post by super mushroom on 2012-04-09
Its an Iomegia eGo helium hdd for mac and pc but on the back it says Drive must be reformatted for use with pc. I bought the external drive new on Amazon and haven't used it before,
Ran sudo parted -l and got the same results.

---

### Post by coffeecat on 2012-04-09
> **super mushroom said:**
> Ran sudo parted -l and got the same results.

OK - I think we can assume that there's no valid partition table at all. Perhaps when you ran fdisk the first time, something went wrong and it erased the partition table. I think that will have to remain a mystery because...

> **super mushroom said:**
> Its an Iomegia eGo helium hdd for mac and pc but on the back it says Drive must be reformatted for use with pc.

Which means that it would have had a GUID partition table and a partition formatted HFS+. Windows 7 (and Vista if I remember correctly) can cope with GPT but not HFS+. Hence the notice that it needs formatting for a PC. When they say PC, they means Windows. Ubuntu can read a HFS+ filesystem on a drive with a GPT, but it's not ideal since you will run into permissions problems and Ubuntu can only mount the journalled version of HFS+ read-only. You have to disable the journal for Ubuntu to be able to write to HFS+. HFS+ is only worth bothering about in Ubuntu if you need to transfer files between a Mac and Ubuntu. Which is probably beside the point for you.

I'm presuming you don't have any data on that drive that needs rescuing. If not, you can reformat it with Disk Utility in Ubuntu. Open Disk Utility. Is your 500GB drive shown as /dev/sdb? Click on it in the left pane. Does it show "Unknown" under volumes? If so, click on "Format Volume". A "Format whole disk" window will open defaulting to the ext4 filesystem. If you intend to use this only in Linux, that is what you need. Make sure the "take ownership of the filesystem" box is ticked, and type in a suitable partition label in the "Name" field. Click on the format button and you should then have a usable drive with Ubuntu.

If you need to use the drive with Windows as well, you will need to format the drive NTFS. When you open the "Format whole disk" window, change "type" to NTFS in the dropdown. If you need to use this drive with a Sony PS3 (and some other devices) you will need FAT32, but FAT32 is an old filesystem with certain limitations. Post back if you need any help.

The "take ownership of the filesystem" for ext4 should prevent permission problems, but if you do run into any with the re-formatted drive, post back and I can take you through the chmod command to fix this if you need.

---

### Post by super mushroom on 2012-04-09
Thanks for all the information, I followed your guidelines step by step and it Works!

thanks coffeecat!

---

### Post by coffeecat on 2012-04-09
Excellent. Good luck!

---

