---
title: "Don't have type for new partition ubuntu"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by mrastko on 2012-11-04
When i try to install ubuntu 12.04 and want to format partition i don't have option "type for new partition ubuntu", so i cant choose primary or logical partition.
Also in gparted when i want to format partition i cant choose those 2 options.
Does anybody knows what is problem?
Thx.

---

### Post by oldfred on 2012-11-04
Welcome to the forums.

Do you have a typical Windows 7 install that uses all 4 primary partitions, so then you cannot create any new partitions?

Post this:

sudo fdisk -lu

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by mrastko on 2012-11-05
I have regulary installed Windows 7 and try to install uBuntu with usb.
But before this happend my friend installed me uBuntu 12.10, dual boot with Win 7, but it had bugs so i remove it and want to install 12.04.
And now i cant choose otption for which type of disk it is. Logical and primary partition stays with silver color like it is locked. I can make partition but dont have that options to choose type.


> **oldfred said:**
> Welcome to the forums.

Do you have a typical Windows 7 install that uses all 4 primary partitions, so then you cannot create any new partitions?

Post this:

sudo fdisk -lu

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by newb85 on 2012-11-05
Could you provide a couple screenshots to give us more details of what partitions are on your HDD and what you're seeing?

---

### Post by mrastko on 2012-11-05
> **newb85 said:**
> Could you provide a couple screenshots to give us more details of what partitions are on your HDD and what you're seeing?

Ok, i will do that in the evening. By the way how i can do it in linux? :)

---

### Post by mrastko on 2012-11-05
> **mrastko said:**
> I have regulary installed Windows 7 and try to install uBuntu with usb.
But before this happend my friend installed me uBuntu 12.10, dual boot with Win 7, but it had bugs so i remove it and want to install 12.04.
And now i cant choose otption for which type of disk it is. Logical and primary partition stays with silver color like it is locked. I can make partition but dont have that options to choose type.


when i type that i get this 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x606a8144

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   307202047   153600000    7  HPFS/NTFS/exFAT
/dev/sda2       307202048   976769023   334783488    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04149828

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdc: 4083 MB, 4083351552 bytes
128 heads, 63 sectors/track, 989 cylinders, total 7975296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          56     7975295     3987620    c  W95 FAT32 (LBA)

---

### Post by mrastko on 2012-11-05
first 2 pictures are from gparted and when i want to choose type of partition it is silver locked. Third picture is from installation guide and there isn't options at all to choose type of partition.

---

### Post by oldfred on 2012-11-05
Please attach screenshots with the paperclip icon in edit panel above your message.

Are you using a liveCD either Ubuntu or a gparted liveCD? 

Your sdb is gpt. It has the advantage that you do not have extended nor logical partitions, but you do have to create a tiny 1MB, unformated bios_grub partition for grub to install to sdb correctly.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Post this since fdisk does not work with gpt partitioning.

sudo parted /dev/sda unit s print

---

### Post by mrastko on 2012-11-06
> **oldfred said:**
> Please attach screenshots with the paperclip icon in edit panel above your message.

Are you using a liveCD either Ubuntu or a gparted liveCD? 

Your sdb is gpt. It has the advantage that you do not have extended nor logical partitions, but you do have to create a tiny 1MB, unformated bios_grub partition for grub to install to sdb correctly.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Post this since fdisk does not work with gpt partitioning.

sudo parted /dev/sda unit s print


I am using bootable usb with ubuntu - live
I attached 3 pictures
1st pic is from installation of ubuntu, as you can see there is no options for type of disk
2nd and 3rd pics are from gparted program, and you can see it is locked options
but for me it is strange that on th first pic there is free partition 160gb and on third pic it is 150gb

---

### Post by oldfred on 2012-11-06
MB or MiB? First is MB others or MiB.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

You still need 1MB (or really 1MiB ? I get confused also) bios_grub partition without any format.

---

### Post by mrastko on 2012-11-06
> **oldfred said:**
> MB or MiB? First is MB others or MiB.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

You still need 1MB (or really 1MiB ? I get confused also) bios_grub partition without any format.


I was meaning that size of unllocated partition in gparted writes 150Gb and in instalation wizard 160Gb

---

