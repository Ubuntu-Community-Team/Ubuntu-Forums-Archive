---
title: "Different partitions being showed in install screen"
date: 2019-09-10
forum: New to Ubuntu
---

### Post by orkop465 on 2019-09-10
Hello, I am currently trying to install Ubuntu from a USB. In Windows I have 210GB unallocated which I wanted to install Ubuntu on, however when I press "something else" in the install menu I see two drives both 512gb with similar names. I ran fdisk -l in a terminal and there I also see these two 512gb drives and not my 210GB free space and 1219GB C: drive. Any help appreciated.

---

### Post by The Cog on 2019-09-10
Can you post the output from **[FONT=Courier New]sudo fdisk -l[/FONT]** here so we can look at it. Otherwise, it's just a guessing game.

---

### Post by oldfred on 2019-09-10
Linux does not use "drives" in the way that Windows does. Those are really partitions.
In Linux a drive is sda, sdb, sdc etc or newer NVMe. And partitions are the number at the end like sda3, sdb2 etc. In Windows sda3 could be a d: drive or sdb2 could be a d: drive.

Post this:
sudo parted -l

What version of Windows? 
If Windows 7 & BIOS/MBR, you have have the 4 primary partition limit.
If Windows 8 or 10 in UEFI mode, you may have fast start up still on. 
If Windows 10 as upgrade from Windows 7 and in BIOS boot mode, you have both issues.

---

### Post by orkop465 on 2019-09-10
```
sudo fdisk -l output:
Disk /dev/loop0: 1.9 GiB, 1987817472 bytes, 3882456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme1n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.6 GiB, 15682240512 bytes, 30629376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00013dfe

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 30629375 30627328 14.6G  c W95 FAT32 (LBA)


Disk /dev/loop8: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```


```
sudo parted -l output:
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sda: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.7GB  15.7GB  primary  fat32        boot, lba


Error: /dev/nvme0n1: unrecognised disk label
Model: INTEL SSDPEKKW512G8 (nvme)                                         
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/nvme1n1: unrecognised disk label
Model: INTEL SSDPEKKW512G8 (nvme)                                         
Disk /dev/nvme1n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```


I have Windows 10, was not upgraded from Windows 7.

The names of the two drives that appear in the install menu are:
/dev/nvme0n1
/dev/nvme1n1
and both appear to be 512.1GB

Thanks for the assistance.

---

### Post by The Cog on 2019-09-10
My guess is that you have two 512GB drives that windows has somehow combined using some kind of software raid-0 arrangement. The drives don't have proper partition tables, so I guess the entire drive (both) are formatted in some proprietary (and probably secret) format.
Unless someone more familiar with windows disk formats than I am knows better.

---

### Post by oldfred on 2019-09-10
This says same as what The Cog says:

Partition Table: unknown

If Intel RST and not RAID 0, you can maybe change to AHCI. But if RAID 0 that will totally break your system. Be sure to have good backups.

---

### Post by orkop465 on 2019-09-11
[SIZE=2]Do you guys have any advice on what I can do to maybe work around this? If my drive is split into two shouldn't Linux still see the free space on one of them? If it helps the model laptop I'm on is [/SIZE][B][SIZE=2][FONT=inherit]ASUS ROG G703GX-XS98K

[/FONT][/SIZE][/B][SIZE=2][FONT=inherit]Do you guys maybe [/FONT]recommend[FONT=inherit] trying to make a persistent Ubuntu USB stick instead and running from that? I have access to a computer with Ubuntu.[/FONT][/SIZE][SIZE=2][FONT=inherit][/FONT][/SIZE]

---

### Post by The Cog on 2019-09-11
I don't think there is anything we can do with those two drives, because Linux cannot even recognise the partition table. We have no clue what is on them let alone which parts (if any) are unused. So in this case, I think a persistent USB stick or a Linux install inside virtualbox running in windows would be your best bet. Or if possible, adding a new third drive to the computer to install Linux on. 

Be careful with terminology - in your first post you talk of unallocated space, but in #7 you talk of free space. To my mind these are different things, with unallocated space being space that does not contain a filesystem (such as not yet allocated to a partition), and free space being space within a given filesystem that is not currently storing file contents.

---

### Post by orkop465 on 2019-09-11
Ah understood. Thanks for the assistance.

---

