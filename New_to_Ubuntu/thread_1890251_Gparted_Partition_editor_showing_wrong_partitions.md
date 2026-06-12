---
title: "Gparted Partition editor showing wrong partitions"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by varundua on 2011-12-03
Hi 

I have windows 7 installed on my machine Dell XPS ( amd 64 ). The partitions on my windows machine are
1. Recovery Disk (around 10 GB)
2. System Reserved (100 MB)
3. Windows Installation Directory (100 GB)
4. Windows Partition (102 GB)
5. Unallocated space (around 256 GB)
 There is one more partition of 196 MB which I don't know what it is for.

I tried to install ubuntu 11.10 using a USB stick. But when i try the option "manualy partition the drive" it shows wrong partitions. Please help, I am pasting here the output of gparted Partition disk, gdisk and Disk utility. 

output of gdisk -l /dev/sda

> 
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Exact type match not found for type code DE00; assigning type code for
'Linux filesystem'
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): BC995C1E-5146-4ECF-B0EC-7233C8DA465A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 746704940 sectors (356.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63          401624   196.1 MiB   8300  Linux filesystem
   2          401625        19535871   9.1 GiB     4200  Windows LDM data
   3        19535872        19740671   100.0 MiB   4200  Windows LDM data
   4        19740672       230068223   100.3 GiB   4200  Windows LDM data

[IMG]http://postimage.org/image/dof9l86z5/[/IMG]

[IMG]http://s8.postimage.org/kevqunu51/Screenshot_at_2011_12_03_09_36_34.png[/IMG]
Please help ?

---

### Post by westie457 on 2011-12-03
Hello varundua. Welcome to the Forum.

It looks like you have the maximum number of partitions (4) allowed with a MBR partition table. To confirm this could you post the output of ```
sudo fdisk -l
``` please. The l is a lower-case L.

Further advice and questions will come after that.

Thank you.

---

### Post by johnny678 on 2011-12-03
The Ubuntu partition which is your 4th primary partition needs to deleted so you can create and extended partition. Once you have created an extended partition you will be able to create a swap, a root partition and a home partition.

eg;

swap ( one a half times your RAM)
/ (10GB should be ok)
home (is really up to you, at least 20GB)


You should also create a Data partition as well that is formatted with ntfs (ntfs-3g) so you can access Data from both windows and linux with minimum hassle.

The four partitions will be created within the extended partition.

---

### Post by westie457 on 2011-12-03
> **johnny678 said:**
> The Ubuntu partition which is your 4th primary partition needs to deleted so you can create and extended partition. Once you have created an extended partition you will be able to create a swap, a root partition and a home partition.

eg;

swap ( one a half times your RAM)
/ (10GB should be ok)
home (is really up to you, at least 20GB)


You should also create a Data partition as well that is formatted with ntfs (ntfs-3g) so you can access Data from both windows and linux with minimum hassle.

The four partitions will be created within the extended partition.

At first glance that is looking correct, however the OP says there is another partition on the hard drive. Without knowing the correct information that has been asked for just deleting partitions might not be the best thing to do.

---

### Post by johnny678 on 2011-12-03
I think you are right about that. The 100mb looks like a a windows 7 boot partition and the partition labelled ubuntu looks like the main windows 7 partition which may have been already wiped. I  don't want to make it complicated for the new user but is a worth mention. Windows 7 can be installed on a single primary partition. I always do it this way. If you do reinstall windows 7 i suggest you install on a single partition. Did you install windows 7 yourself? Do you have a valid installation key sticker on your pc or notebook?

---

### Post by varundua on 2011-12-03
Thanks a lot
 
 Here is the output of the command **fdisk -l**
 
 > 
 ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
 
 Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0xb8000000
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1              63      401624      200781   de  Dell Utility
 /dev/sda2          401625    19535871     9567123+  42  SFS
 /dev/sda3   *    19535872    19740671      102400   42  SFS
 /dev/sda4        19740672   230068223   105163776   42  SFS
 
 
 I don't know whether this would be helpful or not but I ran the command cat /proc/partitions and the result is
 
 > ubuntu@ubuntu:~$ cat /proc/partitions
 major minor  #blocks  name
 
    7        0     678700 loop0
    8        0  488386584 sda
    8        1    9566208 sda1
    8        2     102400 sda2
    8        3  105163776 sda3
    8        4  107110400 sda4
    8       16    3915776 sdb
    8       17    3915772 sdb1
 
 
 From here It is clear that 
sda1 is Recovery (10 GB) 
sda2 is System Reserved (100 MB)
sda3 is my windows Installation
and sda4 is my 4th windows Partition (labelled Ubuntu).

Thanks a lot for helping

---

### Post by varundua on 2011-12-03
> **johnny678 said:**
> I think you are right about that. The 100mb looks like a a windows 7 boot partition and the partition labelled ubuntu looks like the main windows 7 partition which may have been already wiped. I  don't want to make it complicated for the new user but is a worth mention. Windows 7 can be installed on a single primary partition. I always do it this way. If you do reinstall windows 7 i suggest you install on a single partition. Did you install windows 7 yourself? Do you have a valid installation key sticker on your pc or notebook?

But then why it showing the wrong sizes. When I boot into windows I can see the correct partitions. I had windows preinstalled on my laptop and the partitions were there (Recovery, 2 System Reserved partitions and Windows Installation). Also I had red hat installed in another partition. But then due to a system crash I formatted my windows installation as well as red hat installation and reinstalled windows without changing the other partitions. 

I can format the entire disk and reinstall everything from scratch if that is the only solution.

---

### Post by johnny678 on 2011-12-03
Since you have a valid windows 7 key, i would reformat your hard disc with gparted live.  Create one primary partition that will be your windows 7 partition. Make at least one extended partition that will be the bulk of your hard disc space. Create your Linux partitions within the extended. Don't leave any space avaible. Reinstall windows 7 in the ntfs partition you made available. Finally install Linux. 


You don't need the system recovery partition. Make a backup of the windows 7 partition with an imaging tool in case you want to recover it.

---

### Post by westie457 on 2011-12-03
At the moment you have a 'dynamic disk' which is something that only Windows can understand and use. It is possible to convert it back using software however there is no guarantee that it will work. Take a look at this link [http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)

Back up what you want/need to keep before doing anything, regardless of the process working or not. Having backups or your files on a separate partition or hard drive or cd/dvd is a good idea and never too soon to do.

First suggestion is to backup the 'system reserved' partition.
Second suggestion is to make a Windows recovery disk if you do not have a Windows install disk.
Both of the above are probably best done using Windows.

If the info in the link does not work for you then the best thing to do re-partition and format the hard drive and start again.

I will stress this **do not do anything without having the back ups**.

Any further advice needed just ask.

Hope this helps.

---

### Post by Mark Phelps on 2011-12-03
You don't really NEED the boot partition for Win7 -- IF you move the boot loader files into the Win7 OS partition.  An easy way to do that is to install EasyBCD from NeoSmart technologies, and use the option that app provides to move your boot loader files into the Win7 OS partition.  That will allow you to boot without having the Win7 boot partition.

Then, download and install the FREE version of Macrium Reflect, and use the option to create a Linux Boot CD.  Then back off your Win7 OS partition to an external drive.  NOW you have a way to restore your current Win7 OS and no longer need the Recovery partition -- which you can remove using Win7 Disk Management utility.

After that, you should download an burn the Partition Wizard Boot CD (Windows app).  Boot from that and use it to move your partitions to the left, using up the free space, so that all the free space is now on the right.  The the free space unallocates.

And finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in very handy later, should you need to restore your Win7 boot loader.

---

### Post by oldfred on 2011-12-03
As westie457 noticed you have dynamic partitions. His link to using testdisk has worked for some. You used Windows to create more than the 4 primary partitions and it automatically changes to dynamic. 

Per Microsoft it is a one way conversion and you have to totally backup (which you should do anyway) and totally repartition. Then restore data.

Some more info on dynamic partitions:

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard MiniTool to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

---

### Post by westie457 on 2011-12-03
@oldfred

I was not referring to 'testdisk' in the link posted. There is another one there which I neglected to mention and should have. There is a link to this 'work around' [http://support.microsoft.com/kb/913964](http://support.microsoft.com/kb/913964)
Written for XP it might/should work under Vista or 7 when run in compatibility mode. Never having used it I cannot say for definite that it does work.  
To be honest I would try this if I had to but only after back ups had been made.

---

### Post by varundua on 2011-12-03
Thanks everyone :)

Posting from my installed ubuntu. I chose the easy way (Formatted my windows Partition and installed windows and ubuntu side by side ) since I mistakenly formatted my windows boot partition. 

Thanks a lot

---

