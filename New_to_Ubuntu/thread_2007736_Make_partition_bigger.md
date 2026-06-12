---
title: "Make partition bigger"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by hayloiuy on 2012-06-21
Hey guys, I wanna increase the partition size in dev/sda2 which contains Bactrack5. dev/sda2 is the second block from the left.
[IMG]http://img819.imageshack.us/img819/9500/screenshotat20120621213.png[/IMG]

The resize option only enable me to make it smaller not bigger. How can I make it bigger?

---

### Post by hayloiuy on 2012-06-21
Ok I think I found a way around this. I moved the dev/sda4 containing Ubuntu by 100GB forward.  Then bad news. 
I can't move sda2 because sda3 is blocking and I cant resize sda3. What is sda3 anyway? How can I resize it?
[IMG]http://img441.imageshack.us/img441/4555/screenshotdevsdagpartedl.png[/IMG]

This is my fdisk -l output. 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d6a94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/sda2           12749       18827    48827392   83  Linux
/dev/sda3           18827       19800     7812096   82  Linux swap / Solaris
/dev/sda4           19800       38036   146484224   83  Linux

```

---

### Post by Kakers on 2012-06-21
Are you doing this while logged in to Ubuntu? You'd probably find it a lot easier using a Ubuntu or a gparted live cd.

---

### Post by aromo on 2012-06-21
sda3 is your swap partition.  Yeah, you better boot with gparted live CD and move the swap to the end (right) of your disk if you haven't settled your disk layout.

Mine for instance is something like
sda1 => 1 GB => /boot
sda2 => 2 GB => swap 
sda3 => 8GB => /
sda4 => rest of the disk => /DATA (home folders and shared data)

The latest 2 partitions are the most likely to be resized.

---

### Post by hayloiuy on 2012-06-21
Okay guys, I decided to use GParted live cd to move my swap partition. But before I do so I did some research on what to do after moving the swap partition.

According to here:
[http://ubuntuforums.org/showthread.php?t=1811742](http://ubuntuforums.org/showthread.php?t=1811742)

I need to update my swap uuid in fstab file after the swap partition is moved.

Problem is I can't find my swap partition with blkid command.

```
hayloiuy@hayloiuy-G41MT-S2PT:~$ sudo blkid
[sudo] password for hayloiuy: 
/dev/sda1: UUID="285049C15049968A" TYPE="ntfs" 
/dev/sda2: UUID="c4bb733c-7d94-4e35-a5d9-6bddfbcad6b9" TYPE="ext4" 
/dev/sda4: UUID="4b419fbb-e40a-4f56-97b4-85f0e02600e3" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="c5780c48-ec78-4c4d-ae00-85d3036d5cfb" TYPE="swap"
```

I don't think its cryptswap1 because when I opened the fstab file,
the swp uuid is different with cryptswap.
The fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=4b419fbb-e40a-4f56-97b4-85f0e02600e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=0d3a3df7-3d6d-4acd-9454-f531fab5e111[COLOR="YellowGreen"][/COLOR] none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

My question is where is my swap UUID.

Note that all this information is obtained from before I move the swap partition.

---

