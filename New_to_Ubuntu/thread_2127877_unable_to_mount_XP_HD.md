---
title: "unable to mount XP HD"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by Aurie72 on 2013-03-21
Newbie here, first let me say thanks for taking your time and helping me out. 
PC won't boot up under XP, and the person don't want to lose data.
I've read that under Ubuntu I might salvage this person data. 
What I have tried so far:

ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk

root@ubuntu:~# fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
86 heads, 15 sectors/track, 484606 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           0   268435454   134217727+   4  FAT16 <32M


root@ubuntu:~# mount -t vfat -o unmask=000 /dev/sda1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg | tail
[   56.476386] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[59502.180441] FAT-fs (sda1): Unrecognized mount option "unmask=000" or missing value
[59986.230858] EXT3-fs (sda1): error: can't find ext3 filesystem on dev sda1.
[59986.231224] EXT4-fs (sda1): VFS: Can't find ext4 filesystem
[59986.231485] FAT-fs (sda1): invalid media value (0xb9)
[59986.231490] FAT-fs (sda1): Can't find a valid FAT filesystem
[59986.243141] ISOFS: Unable to identify CD-ROM format.
[59986.243631] SQUASHFS error: Can't find a SQUASHFS superblock on sda1
[60133.380363] FAT-fs (sda1): Unrecognized mount option "unmask=OOO" or missing value
[60149.660408] FAT-fs (sda1): Unrecognized mount option "unmask=000" or missing value
root@ubuntu:~# mkdir -p /media/disk
root@ubuntu:~# mount -t vfat -o iocharset=utf8,unmask=000 /dev/sda1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then after more research I found another command and gave that one a try:

root@ubuntu:~# mkdir -p /media/disk
root@ubuntu:~# mount -t vfat -o iocharset=utf8,unmask=000 /dev/sda1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg |tail
[59502.180441] FAT-fs (sda1): Unrecognized mount option "unmask=000" or missing value
[59986.230858] EXT3-fs (sda1): error: can't find ext3 filesystem on dev sda1.
[59986.231224] EXT4-fs (sda1): VFS: Can't find ext4 filesystem
[59986.231485] FAT-fs (sda1): invalid media value (0xb9)
[59986.231490] FAT-fs (sda1): Can't find a valid FAT filesystem
[59986.243141] ISOFS: Unable to identify CD-ROM format.
[59986.243631] SQUASHFS error: Can't find a SQUASHFS superblock on sda1
[60133.380363] FAT-fs (sda1): Unrecognized mount option "unmask=OOO" or missing value
[60149.660408] FAT-fs (sda1): Unrecognized mount option "unmask=000" or missing value
[62315.725172] FAT-fs (sda1): Unrecognized mount option "unmask=000" or missing value


Can someone help me mount this drive?
this is a dell e310, not sure if model of pc needs to be given, but thanks once again.

---

### Post by Mark Phelps on 2013-03-22
Are  you running Ubuntu on the drive from which you are trying to recover data?  IF so, you would have better results if you either (1) ran Ubuntu from a LiveCD, or (2) ran Ubuntu from another hard drive, with the bad drive connected to that PC.

Also, to mount the Windows partitions, you don't need to issue a mount command; instead, all you have to do is click on the "home" icon on the top-left of the navigation panel and select from the list of filesystems.

---

