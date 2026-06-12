---
title: "installing ubuntu on a partition that was created by windows"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Stack15 on 2012-06-25
hello ubuntu gurus,
please help me installing linux
i want to install ubuntu on a desired partition of my hard drive. i have Windows 7 installed on one of the partitions. basically i have 320 GB hard disk and it is divided into 4 partitions as follows:
partition 1 (50 GB) -- C: Windows 7
partition 2 (82 GB) -- D: [left for installing ubuntu]
partition 3 (82 GB) -- E: [used to keep my files, etc.]
partition 4 (84 GB) -- F: [also used to keep files like softwares & other stuff]

i have created a bootable usb disk for installing ubuntu using Universal usb installer. i have installed plop boot manager to make my system boot from usb disk, because my bios does not support usb boot.

now the ubuntu installation part, i want to install ubuntu onto the D drive. and for that, i selected the option "install ubuntu alongside windows 7", but after that step, i don't know what to do. Don't want to loose data on the E & F drives. i have posted images of the installation. please help me and guide me through the installation. also, i want to learn how it works.
any kind of info is appreciated.

(sorry for bad english) :-#

---

### Post by critin on 2012-06-25
You should choose 'Something Else' and clearly choose the partition you want.  If you go with installing side-by-side choice, you're losing the other partitions.  See your screenshots for verification of the size that each system will end up with.   Two partitions are shown with that choice, and they aren't the sizes you listed.

Windows has only 1.5 G free--it may be slow and have very little room to expand.

---

### Post by carl4926 on 2012-06-25
You should have chosen the something else option
And used the advanced partitioner
Setting the partition you call D to be the install partition

But you don't have a swap partition either?

Can you please boot the live cd to the live desktop and open a terminal and post the result of

```
sudo fdisk -l
```Then we can make sense of your partitioning. That windows info is next to useless

---

### Post by critin on 2012-06-25
Studying up on partitions is pretty important.  This link looks good.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Bucky Ball on 2012-06-25
Welcome.

Delete partition 2 (D). Choose 'Something else' during install. Create an extended partition with the free space left by deleting D.

You can now create three logical partitions inside the extended for Ubuntu and they are defaults in the partitioner:

/ = root, OS, 15-20Gb fine;
/home = your personal stuff, big as you like leaving room for;
/swap = 2Gb fine.

For /home, rather than using the default /Video, /Documents etc. directories you may want to delete them and create symlinks to existing folders which already hold Videos, Documents etc, in which case this partition doesn't need to be very big (or in fact be there at all as it would then be created as a /home directory inside / which you could fill with symlinks to other existing directories). 

You can only have four primary partitions on one physical drive; thus the extended partition which allows you to create as many logical partitions inside it as your hardware can handle. ;)

---

### Post by nipunshakya on 2012-06-25
seeing at your partition, it looks good(though c: and e: are full enough)....
from the second image of yours, select the 'something else' option...
after that, choose drive d:(d: naming will not be shown so you have to assume the free disk yourself)... format it as logical, and then make 3 partitions within it as /,/home and swap as 20,60 and 2 gb respectively space allocations... select the extended partition to be formatted, and select /dev/sda as the place for your boot loader to be installed and you are good to go...

Goodluck

---

### Post by Stack15 on 2012-06-25
@carl4926 - these are the results 
------------------------------------------------
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95349534

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048   104859647    52428800   42  SFS
/dev/sda3       104859648   625140399   260140376   42  SFS

Disk /dev/sdb: 3918 MB, 3918495744 bytes
255 heads, 63 sectors/track, 476 cylinders, total 7653312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bc41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7653311     3826624+   c  W95 FAT32 (LBA)
-------------------------------------------------------------

i appreciate your replies: @critin and @Bucky Ball and @WinuxUser
i will try it

---

### Post by Stack15 on 2012-06-25
when i click "something else option"
i get the same option as in Screenshot number 4

-----------------------------------

plus, i have one more major problem, i can't connect to internet when using live desktop.
i have a PPPoE internet connection. in windows 7 it is working fine. but it's not working in live desktop. at first, live desktop does not recognize the Ethernet connection, but after manually editing the gateway, ip and netmask, it is connected to the router but still not connected to internet. 
everytime i have to again boot up to windows 7 and get online to view this forum.

---

### Post by oldfred on 2012-06-25
Your fdisk shows SFS not NTFS. SFS is dynamic partitions which does not work with Ubuntu. Windows auto converts from the basic 4 primary partitions to SFS when creating more than 4 partitions,  not creating an extended partition with logicals, but Windows does work with logical partitions.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

