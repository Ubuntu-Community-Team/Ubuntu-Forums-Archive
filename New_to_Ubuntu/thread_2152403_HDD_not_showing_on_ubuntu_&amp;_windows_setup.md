---
title: "HDD not showing on ubuntu &amp; windows setup"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by chayanman on 2013-06-07
I tried to install ubuntu 12.04 on my pc running windows 7 . At first i created a bootable flash drive & run ubuntu setup. Then i breakup the partition of C drive to make space for ubuntu. After that ubuntu is showing my partitions but i can't install ubuntu on it, it is showing a notification that the HDD is busy. Even when i'm trying to install windows from boot, no HDD is being shown. I can see my HDD from BIOS. Please reply as soon as poosible. Thanks in advance.

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]chayanman; Hi !

What is your install procedure ? Is the device you are installing from set as the 1st boot priority in your bios ?

Sounds like you are still booting into your hard drive, no can do - to install - as the hard drive is in use.
[/COLOR][INDENT=3][COLOR=#000000]
just my thought

[/COLOR][/INDENT]

---

### Post by chayanman on 2013-06-07
Thnx for your reply. My boot priority is set as : 1.cdrom>2.hdd. I can see all my drives from live cd but i can't install ubuntu on any of the partitions and even while i'm trying to install windows i can't see any drives. I've some important data on my HDD so i can't format it from live cd. I guess its a partition & mbr related problem. As i'm quite novice here,some help will be highly appreciated.

---

### Post by Bashing-om on 2013-06-07
chayanman;
My pleasure to help...let us see what we are working with, post the output of terminal codes from the liveCD :

```
sudo fdisk -lu ##from live cd<-disk info
sudo parted -l ##from live cd<-disk info
sudo parted /dev/sda unit s print ##from the liveCD

``` so that nothing is mounted on the harddrive,
then we see about installing grub onto the hard drive and getting Window's picked up from ubuntu's grub.
[INDENT=3]
it is all a learning experience

[/INDENT]

---

### Post by chayanman on 2013-06-08
Here are the results :

> **ubuntu@ubuntu:~$ sudo fdisk -lu**
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd644fa38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20000767     9999360   83  Linux
/dev/sda2        75976626   976771119   450397247   42  SFS
/dev/sda3        20000768    24000511     1999872   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8166 MB, 8166703104 bytes
35 heads, 32 sectors/track, 14241 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1888    15950591     7974352    b  W95 FAT32



> **ubuntu@ubuntu:~$ sudo parted -l**
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  10.2GB  10.2GB  primary
 3      10.2GB  12.3GB  2048MB  primary
 2      38.9GB  500GB   461GB   primary


Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sdb: 8167MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      967kB  8167MB  8166MB  primary  fat32        boot


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.



> **ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print**
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End         Size        Type     File system  Flags
 1      2048s      20000767s   19998720s   primary
 3      20000768s  24000511s   3999744s    primary
 2      75976626s  976771119s  900794494s  primary



**The following error has been kept showing when i run ubuntu installation & gparted :

> Error informing the kernel about modifications to partition /dev/sda2 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Failed to add partition 2 (Device or resource busy)

/dev/sda2 is shown to be all my drives containing data (except C drive).

Thanks once again for your help.

---

### Post by Mark Phelps on 2013-06-08
I'm presuming that you "broke up your C: drive" using the Win7 Disk Management tool, right.  What you appear to have done is created one to many drives (actually, they are partitions, not drives) -- because the report says "SFS", which I believe is what that tool calls the Windows Dynamic Disks.  Linux can't handle Dynamic Disks, so it won't be able to install in that situation.

You created quite a mess by charging ahead like this.  You will need to remove the partition you created and not try to create it again.

You need to look at the partitions in Win7 Disk Management and see how many you have.

---

### Post by Bashing-om on 2013-06-08
Yaahhh Mark, that cuts right to the meat of the matter !
[INDENT=2]
work to-be done

[/INDENT]

---

### Post by chayanman on 2013-06-14
Soory for being late guys as i was out of internet for few days. I followed your suggestion & backed up all my data. Then format the whole hdd & then install precise pangolin. Feeling great to be back in the ubuntu community after a few years. Thanks mates for helping.     :)

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]chayanman; Hey ......
Great you are back up and running .
Our pleasure ( putting my foot in Mark's mouth)... to be of assistance.. We trust you will make your contributions as you are able.

 Please mark this thread as "solved", aides others seeking solution, and helps keep the forum tidy.

 [/COLOR]> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2]
see ya !

[/INDENT]

---

