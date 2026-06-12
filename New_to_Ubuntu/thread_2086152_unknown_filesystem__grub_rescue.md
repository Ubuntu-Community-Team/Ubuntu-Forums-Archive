---
title: "unknown filesystem : grub rescue"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by anurag7 on 2012-11-20
Hi all, I have a single boot system with Ubuntu 11.10 and i'm unable to boot into it due to error unknown filesystem : grub rescue at prompt. 
I tried to repair grub with a live usb stick as per the steps i found on forums but could not proceed further. These are the outputs of some of the commands:

**sudo fdisk -l**

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f28c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   972847103   486422528   83  Linux
/dev/sda2       972849150   976771071     1960961    5  Extended
/dev/sda5       972849152   976771071     1960960   82  Linux swap / Solaris

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7821311     3910640    b  W95 FAT32

**sudo fdisk -l /dev/sda1**

Disk /dev/sda1: 498.1 GB, 498096668672 bytes
255 heads, 63 sectors/track, 60556 cylinders, total 972845056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table
[B]
sudo mount /dev/sda1 /mnt[/B]
mount: you must specify the filesystem type

**sudo mount -t ext4 /dev/sda1 /mnt**
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**dmesg|tail**
[   66.881963] wlan0: associated
[   66.889048] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.024032] wlan0: no IPv6 routers present
[  475.357268] EXT3-fs (sda1): error: can't find ext3 filesystem on dev sda1.
[  475.366696] EXT2-fs (sda1): error: can't find an ext2 filesystem on dev sda1.
[  475.373330] EXT4-fs (sda1): VFS: Can't find ext4 filesystem
[  475.388623] FAT-fs (sda1): invalid media value (0x00)
[  475.388629] FAT-fs (sda1): Can't find a valid FAT filesystem
[  475.404278] SQUASHFS error: Can't find a SQUASHFS superblock on sda1
[  481.117560] EXT4-fs (sda1): VFS: Can't find ext4 filesystem


I'm pretty much a newbie to linux. It looks like the partition /dev/sda1 has lost some header information relating to filesystem. Is there any way i can recover from here or if i attempt to reinstall ubuntu on same partition can my data be saved?

---

### Post by Moose on 2012-11-20
Have you made/deleted/edited any partitions since you installed your os?

---

### Post by PowerBarry43 on 2012-11-20
Hi
 
You could try downloading a supergrub boot disk which would allow you to boot into your installed Ubuntu if it's intact. from there you could run a sudo update-grub which would probably fix.
 
Hope this helps
 
Barry

---

