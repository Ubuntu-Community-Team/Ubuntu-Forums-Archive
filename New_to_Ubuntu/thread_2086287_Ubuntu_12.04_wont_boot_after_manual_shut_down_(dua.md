---
title: "Ubuntu 12.04 wont boot after manual shut down (dual boot with windows, no wubi)"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by Bweytjens on 2012-11-20
Hi all. I am new to this forum and an absolute beginner. Since yesterday I have this problem that I cant boot ubuntu anymore. It happened because of a manual shut down after the laptop froze up while performing heavy calculations (runnig a problog program). Please help...

PROBLEM STATEMENT

The exact error is in the attached picture. In case it is not readable it states the following:

mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesnt have requested /sbin/init.
No init found. Try passing init= bootarg.

SOLUTIONS THAT DID NOT WORK (always booted from ubuntu live CD using a bootable USB device)

I allready tried a handfull of solutions that did not work:

- sudo fsck /dev/sda5 => Did not work because it stated that sda 5 was not found. Whenever I try sudo fdisk -l it also only shows sdb1 (which is the USB device used for booting) but not a single partition from sda.

-Boot-repair. Succesfully downloaded the Boot-repair program and ran it. It then stated it had fixed some booting problems but ubuntu still has the same problem.

-rescue remix: Used sudo swapoff -a
                    sudo parted /dev/sda
                    rescue START 1 END 6 (since I have 6        partitions on my sda). Did not work because it says it cannot identify sda.

-Gpart: Used gpart /dev/sda. It then already stated it could not find sda(either)

-Ubuntu disk utility: From dash=> Disk Utility I can see my sda partitions but they seem to be inactive since I cannot change their lables, nor scan them

-chkdsk from windows 7. Scanned my c drive from here but this didnt solve the problem either.


ADDITIONAL INFO

Sometimes when trying to acces one of the sda partitions it says I/output error or unable to read from superblock. The laptop does seem to recognize the sda partitions but appears to be unable to acces them from ubuntu

THANKS IN ADVANCE

Any help or suggestions will be greatly appreciated as I would hate to reïnstall all of my programs on ubuntu.

---

### Post by Bashing-om on 2012-11-20
Bweytjens; Hi !

Bad superblock ?
From the liveCD:
```
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo fsck -f /dev/sda1 

```In the event that a bad superblock is confirmed; solution at this link:
[http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04](http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04)
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Bweytjens on 2012-11-20
thank you for the reply.

I ran the commands you suggested and the output was this:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2015230     1007584    6  FAT16
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Model: UDISK PDU15_1G 6AG2.0 (scsi)
Disk /dev/sdb: 1032MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1032MB  1032MB  primary  fat16        boot


ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: /dev/sda: unrecognised disk label      
                            
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 


I also read the possible solution page if it would be due to a bad superblock but when I run one of the first solution steps i get this:

dumpe2fs /dev/sda2 | grep 
superblockdumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: Permission denied while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
Any suggestions? 
Thanks in advance

---

### Post by Bashing-om on 2012-11-20
All things I see relate to windows. 
Back up and regroup; let's see the out put of terminal commands - from the liveCD:
```
sudo fdisk -lu
sudo parted -l

```and see if there is a reference to ubuntu's ext4 file system.
Be advised I expected to see the device "sda"[linux syntaxual for the 1st hard drive] partitioned. As such, question: are you booting from usb  that is labeled as sda ?
Maybe you have ubuntu installed on the usb device rather than the hard drive ?

we are looking for system partitions utilizing the ext4 file system.
[INDENT]kook'n to see what we are looking for <== BDQ

[/INDENT]

---

### Post by Bweytjens on 2012-11-20
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 2015230 1007584 6 FAT16


ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label 

Model: UDISK PDU15_1G 6AG2.0 (scsi)
Disk /dev/sdb: 1032MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 1032MB 1032MB primary fat16 boot


This is what those commands yield. I am indeed booting from a usb drive and use the option 'try ubuntu'. This usb device seems to be labeled sdb since 1032 MB is exactly the size of this drive and none of my hard drive partitions are about 1 GB in size.

Perhaps it is normal I cannot see sda while booting the downloadable iso file from ubuntu 12.04 from a usb stick and then selecting the option to 'try ubuntu' ? Do you recommand another way of trying to acces my hard drive?

thank you,
Bram

---

### Post by Bashing-om on 2012-11-20
bram;
I am at a loss as to why the hard drive is not seen.
I am further handicapped in that I have never used a usb device to boot from.

Let's try this:
from the "try" mode" : launcher ->dash->(search box) enter the term GParted->icon
launches ubuntu's partition manager. LOOK but do not TOUCH until you have read and understand the instructions for use.

In the right upper corner of the utility one is able to select any one device at a time, that is recognized  on the system.
Let's see if the hard drive only contains windows partitions and;
That begs the question; How is ubuntu (ext4 file system) able to install on the usb device (fat16) further complicated with fat16's limitation of 4GB file siszes ?  -> maybe only grub is actually installed to the usb device ???

In any event ..please post the screen shots of GParted.
[INDENT]we will see what is to be seen ==> BDQ

[/INDENT]

---

### Post by Bweytjens on 2012-11-20
I added the screenshot from GParted. It seems that no hard disk is detected (mine should be 500 GB in size. 1 GB is the exact size of the usb stick I am using to boot ubuntu 'try' mode).

I also added a screenshot from the Diskutil in ubuntu, showing that my hard disk actualy exists. But I do not seem to be able to access the hard disk cause SMART status reads it is not supported. (the 101 GB partition should be the partition where my crashed ubuntu version is installed onto while the 380 GB partition should be the windows partition)

This all seems very strange to me. I hope you know what is wrong with it.

Thank you for helping me!

ps: I live in belgium (GMT+1) so I will be going to sleep now. Wont be posting again in the following 15 hours due to having to attend class :)

---

### Post by NikTh on 2012-11-20
> **Bweytjens said:**
> 
ubuntu@ubuntu:~$ sudo parted -l
**Error: /dev/sda: unrecognised disk label **


Hi , 
this can be
1) **HDD is dead - bye bye** 
2) **filesystem - blocks - or table are corrupted**

From Ubuntu-Live you can see and access all your drives . Internal & external . It has nothing to do with this issue. 

We can try somethings , but if HDD is dead , you cannot do much. 
_All bellow attempts will performed from Ubuntu-Live=> "Try Ubuntu"_

**Examine HDD with smart-tools**
Open a terminal and write
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
```
Give the results back here. 
**Try to recover your partitions**
If you care about your data , try to recover partitions and table maybe , with [TestDisk](http://www.cgsecurity.org/wiki/TestDisk). Tutorial step by step can be found here => [TestDisk-Step-by-Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Additional methods to recover data , see here => [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

**Try to reformat the drive**
_If you don't care about your data_ and you only need to make the HDD usable again (if is not dead) , then try to reformat it. 
A good tool is fdisk from terminal and/or gparted (GUI) both included in Ubuntu-Live session.

With fdisk , write in terminal 
```
sudo fdisk /dev/sda
``` and see the results. 

With Gparted , click on Dash (Ubuntu Icon up left , first in launcher) write gparted and see if your disk can be scanned. 

Thanks

---

### Post by oldfred on 2012-11-20
Disk Utility is saying Smart data not supported, but that could be just the drive issues.

That it shows drive and partitions but none of the partition are shown with any formats is unusual. 

I would try testdisk first to see if it can show anything.

That e2fsck did not work on sda1 or sda2 is normal. Those would normally be NTFS with a dual boot, and you have to use chkdsk from Windows on NTFS partitions. The e2fsck then should be tried on sda5 if that is the Linux partition, but it also will not work on swap.

---

