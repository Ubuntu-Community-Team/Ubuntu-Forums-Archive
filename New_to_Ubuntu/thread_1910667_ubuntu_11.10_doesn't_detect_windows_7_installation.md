---
title: "ubuntu 11.10 doesn't detect windows 7 installation"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by sawyer03 on 2012-01-17
:p This is my first post:KS.
When i install ubuntu 11.10 using live usb,it doesn't detect  windows 7 installation,:oops:
only erase and something else option comes,somedays ago before that i convert my MBR partition to GPT partition using gdisk for windows,then format my disk using DISKPART,and convert it again in MBR using DISKPART then install windows 7.When i try to install ubuntu it doesn't detect windows 7 then again i delete leftover data of GPT using fdisk,then it detect windows 7,but doesn't show the option "install alongside windows",what will i do pls help me,i m completely beginner pls guide me.  :D

---

### Post by Double.J on 2012-01-17
Hi there! welcome to the forums!

It may be GPT - I use GPT and install alongside doesn't come up on mine either? 

Anway, not a problem, whilst easy, install along side is rarely the best option - it just splits the windows partition in half, even though W7 needs a minimum of 40GB and Ubuntu about half that!.

Have you backed up all your data? if not, do it now.

Once backed up, run the live usb and try not install. press the windows key and in the search box type "gparted" then press enter and the partitioner will pop up

use this to shrink the windows partition from the right to the left, creating free space for ubuntu. I wouldn't advice less than 20GB, but of course a maximum is up to you. Windows must stay to the left, and click apply after each change you make.

Once set up how you want, run the installer and now you should be able to choose use free space :)

Enjoy ubuntu!

---

### Post by Mark Phelps on 2012-01-17
The Ubuntu installer doesn't provide the side-by-side option if it is unable to create a new partition.

This happens in the case where, either you're using GPT, or your drive already has the maximum of 4 Primary partitions (or 3 Primary and one Extended).

To see what you have, boot from the Ubuntu CD, choose the Try Ubuntu option, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on the drive.  Please post that information back here.

---

### Post by sawyer03 on 2012-01-18
Thanks GNU and MARK PHELPS for such a fast reply.
I try what u said GNU but my partition scheme is MBR at present.I can't able to move slider in GPART.
U R right MARK i m using 4 primary partition.
How do i post the result of "sudo fdisk -lu",where i save the output pls tell me.

---

### Post by Double.J on 2012-01-18
Hi there, just copy the text from the terminal into the reply box, then highlight it and click the # button at the top of the reply box :)

In terms of what you are trying to do to the drive, anMBR partition table can only have 4 primary partitions, or as mark said 3+1 extended - that extended partition can hold a large number of logical partitions. Ubuntu and other linux stystems can use these logical partitions, but OS such as windows, OS X and PC-BSD need to be on a primary partition. 

Gparted can convert an mbr partition table to GPT that will allow many (100+) primary partitions, But this would reset the partition table, and is akin to erasing the disk.

if you set up GPT table, you usually add a small (1mb) partition at the start of the drive, formatted as free space and then give it the flag Bios_Grub to allow incompatible OS to treat it as an MBR... but again this is only for starting over.

Sticking with the MBR set up you have, If you have an external HDD it may be simpler to install ubuntu to that? If you have Windows 7 it may also be possible to claim back a primary by getting rid of it's recovery partition - I've seen posts on how to install windows without it, so it may be worth checking over at [seven forums]("http://www.sevenforums.com/") to see it there's a way to remove it from an installed system?

Additionally if one of your primarys is a data partition, it may be possible to copy that data to an external device, delete the partition, created extended, then add logical partitions for ubuntu,swap and a data partition inside the extended?

Whatever you decide to do - make sure everything is backed up on your drive before editing ANY partitions.. just in case something goes wrong.

Failing everything else, if you only have the one drive and everything HAS to stay as is, you could always consider a wubi install?

Hope it helps!

---

### Post by Mark Phelps on 2012-01-18
If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by sawyer03 on 2012-01-18
Hey mark my all disks are Dynamic at present.

---

### Post by sawyer03 on 2012-01-18
Hi there,okay i m ready to format my hard disk at the cost of,i m able to dual boot ubuntu and windows 7.Pls help me from the scratch.

---

### Post by sawyer03 on 2012-01-18
here is the output


buntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d225f2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   553166847   276480000    7  HPFS/NTFS/exFAT
/dev/sda3       553182210  1106155574   276486682+   7  HPFS/NTFS/exFAT
/dev/sda4      1106155575  1501048494   197446460    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4010 MB, 4010803200 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7833600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbb0dee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7833599     3916768+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by Mark Phelps on 2012-01-18
> **sawyer03 said:**
> Hey mark my all disks are Dynamic at present.

Then, Ubuntu-wise, you're basically out of luck.  Linux can't use Dynamic Disks.  

There are ways to convert Dynamic Disks back to Basic Volumes but all the links I've found deal with EMPTY disks, thus, the content is erased.

---

### Post by oldfred on 2012-01-18
Fdisk normally shows sfs as type not NTFS as formating is inside the dynamic partitions which it then cannot see. So it does not look like you have dyanmic partitions.

But if you did anything with gpt, you need to use fixparts to remove the stray gpt data. One advantage of gpt is that it keeps a backup partition table. Older software does not see backup and works, but some of the newer software is gpt aware and then gets confused if drive is MBR but still has backup gpt partition data.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by sawyer03 on 2012-01-18
hey i m able to convert my disc to basic using EASEUS partition manager without erasing data.
before that i m using 4 primary partitions,then i change it to 2 partition then ubuntu detect windows 7.
Thanks to u guys.
pls help me how i make a partition extended.

---

### Post by sawyer03 on 2012-01-18
hey i m giving up i try everything from the net,once when i format my partition and using only 3 primary partition then ubuntu detect windows 7,after that i rearrange my partition i built one primary(system reserved 100 mb) and 1 extended(in it 4 logical partitions) and then i try to install ubuntu again it doesn't show me the option.I m tired right now i have 1 primary and 1 extended then why it doesn't detect windows.

---

### Post by sawyer03 on 2012-01-18
finally hardwork have the taste's of heaven,I rearrange my partitions 3 primary(including 1 system reserved[100mb]) and 1 extended,then boom problem solved i use EASEUS partition manager for that,after that ubuntu also installed in extended partition in the form of primary.THANKS to all of u guys,you r my heroes.
thanku again.....

---

