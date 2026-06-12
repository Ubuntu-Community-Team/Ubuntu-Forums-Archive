---
title: "Interpreting output from fdisk -l on a dual boot ststem"
date: 2018-03-17
forum: New to Ubuntu
---

### Post by chaoticbob on 2018-03-17
Hi. I've recently installed 16.04 on a Dell Optiplex 780 desktop which  was running Windows 7 - I went for the dual boot option and accepted the  default options offered by the installer. It all works fine, but I  don't understand how the disk is partitioned after the installation. At  some point I may want to mount Windows file space on Linux if that is  possible. If anyone can interpret the output of fdisk -l for me I'd be  most grateful:

```
robin@robin-OptiPlex-780:~$ sudo fdisk -l
[sudo] password for robin: 
Disk /dev/sda: 232.9 GiB, 250000000000 bytes, 488281250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x58b028fb

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 312496127 312289280 148.9G  7 HPFS/NTFS/exFAT
/dev/sda3       312498174 488280063 175781890  83.8G  5 Extended
/dev/sda5       312498176 480229375 167731200    80G 83 Linux
/dev/sda6       480231424 488280063   8048640   3.9G 82 Linux swap / Solaris




Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdcbac668

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1          63 224669024 224668962 107.1G  b W95 FAT32
```

I understand the basics of Unix partitioning/mounting, but have no experience of doing this on a hybrid system.

Thanks, Robin

---

### Post by Bashing-om on 2018-03-17
chaoticbob; Sure -

We can have that discussion about the output of 'fdisk' .

Here what is:
the 1st hard drive is identified as sda and has 232.9 GiB of usable space, the sytem(s) take a bit for it's own house keeping.
On this sda device there are a number of partitions.
The first two - sda1 sda2 - are devoted to Windows and are primary partitions.
Now, in this legacy partitioning scheme one can have a MAX of 4 primary partitions - so how do we get around this limitation ( you see  5 patitions ) ..

well - that is where the concept of a "extended" partition comes into play . This is also a primary partition, but it can have an additional 128 " logical" partitions within. In your case this is : 
sda3 as that container to hold the logical partitions:
sda5 as a logical partition of 80 Gigs that is your linux install
sda6 as a logical partition of 3.9 Gigs that is your swap partition 

The second hard drive is identified as sdb ( b==2) .
It is a single partition (sdb1) devoted to a Windows file system ( W95 FAT32). Yes linux can read that file system !
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) <-HowTo: Partitioning Basics-bodhi.zazen

You presently have access to the second drive via the GUI with standard defaults.
Now ff you want access via the text interface; see:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://ubuntuforums.org/showthread.php?t=2337933](https://ubuntuforums.org/showthread.php?t=2337933) (sudodus <- mount drive with full permissions
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[INDENT][INDENT]welcome to the learning curve[/INDENT][/INDENT]

---

### Post by chaoticbob on 2018-03-17
Thanks Bashing-om, very helpful, and I'll follow up the links.
I'm enjoying the learning curve,!
Robin

---

### Post by Bashing-om on 2018-03-17
chaoticbob; :)

When you are ready to continue .

[INDENT][INDENT]we are here to help
[/INDENT][/INDENT]

---

