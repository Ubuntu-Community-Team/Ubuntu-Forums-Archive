---
title: "Installation prob: Ubuntu installed but windows7 not working"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by zak100 on 2013-02-19
Hi,
Thanks for your advise. However i installed linux earlier and it is running but my windows 7 is no more operational.
Code:
 
r-laptop:~$ sudo fdisk -l
[sudo] password for zulfiqar: 
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f916d90
Device Boot Start End Blocks Id System
/dev/sda1 1 1 992+ 42 SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 1 26 203776 42 SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 26 49630 398446592 42 SFS
/dev/sda4 49630 91202 333922168 83 Linux
[EMAIL="zulfiqar@zulfiqar-laptop:~$"]zulfiqar@zulfiqar-laptop:~$[/EMAIL]
 
There were different ouputs from linux fdisk and windows disk management. Former was showing only 4 partitions but later was showing 5 partitions.
I am able to go upto 
(Starting windows) and then it says your windows has been corrupted due to installation of a software.
I dont have bootable disk and the factory fitted installation (i.e F11) is also not working.
Zulfi.

---

### Post by oldfred on 2013-02-19
> /dev/sda1 1 1 992+ 42 SFS

SFS is dynamic partitions. You used Windows to create more than the allowed 4 primary partitions.
Dynamic does not work with Linux and to unconvert you should not have more than 4 partitions.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

