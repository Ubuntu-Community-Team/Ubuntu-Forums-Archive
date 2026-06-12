---
title: "From Ubuntu/ Windows to Ubuntu"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by eduardo saxel on 2011-12-26
Hi there,

My PC runs Ubuntu alongside with Windows. It has its hard disk slit in two. What I would like to do is to eliminate Windows and keep Ubuntu.

Thanks on advance.

---

### Post by BC59 on 2011-12-26
It's not that easy. Maybe your booting system is installed on the Windows partition.
Can you post the result of these commands?

```
sudo parted /dev/sda print
sudo fdisk -l #(it's a lower case L)
```

---

### Post by eduardo saxel on 2011-12-26
bastien@bastien:~$ sudo parted /dev/sda print
[sudo] password for bastien: 
Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  62.9GB  62.9GB  primary   ntfs            boot
 2      62.9GB  320GB   257GB   extended
 7      62.9GB  103GB   40.0GB  logical   ext4
 5      103GB   108GB   4999MB  logical   linux-swap(v1)
 6      108GB   320GB   212GB   logical   ext4

---

### Post by eduardo saxel on 2011-12-26
bastien@bastien:~$ sudo fdisk -l #

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ab37aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7650       38914   251129857    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           12513       13120     4881408   82  Linux swap / Solaris
/dev/sda6           13120       38914   207184896   83  Linux
/dev/sda7            7650       12512    39061504   83  Linux

Partition table entries are not in disk order

---

### Post by BC59 on 2011-12-26
Yes, the boot sector is on the Windows partition.

It's not so easy to do it.
Try to follow the instructions from [here]("https://help.ubuntu.com/community/HowToRemoveWindows") and if you have any question post it.
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

### Post by oldfred on 2011-12-26
It looks like your two systems are separate.

We do have many who come back and want to reinstall Windows as they need that one program or game that does not work in Linux. I would suggest housecleaning, backing up all data and making a total backup of you system to make it possible to reinstall.

What do you want to do with space. It is not particularly easy or safe to move the Linux partition left to use the free space. Often best to make it a data partition or move /home. If you want either you just use gparted to reformat the NTFS partition to ext4 (or ext3).

Backup windows  - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

# MoveHome.txt
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue

---

### Post by eduardo saxel on 2011-12-26
mmmm... live CD or USB stick, which should I choose? Obviously, as I'm a beginner, I don't find any reasons to pick either one or the other.

---

### Post by BC59 on 2011-12-26
It's better to burn a CD. USBs sometimes create problems.

---

