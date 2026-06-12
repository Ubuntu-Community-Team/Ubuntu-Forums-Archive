---
title: "Dual Boot"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by Jimorris on 2012-03-25
When I have tried to install ubuntu along side XP which the start up menu tells me I shall be able to do I get to a screen that says delete XP and install OR do something else !

When I click 'do something else' I get a screen with various options like New partition Table, add,change ,delet,revert and device info e.g. /dev/sda....../dev/sda1 nfs etc

I have no idea what I am supposed to do at this point so any advice and direction much appreciated.

cheers
jim

---

### Post by garvinrick4 on 2012-03-25
Run your install cd in Try Ubuntu instead of install.
when boots open a terminal ctrl/alt/t
```
sudo fdisk -l
``` (lower case L)
```
sudo parted -l
``` (lower case L)

Post the output: (copy and paste in your thread)

---

### Post by centaurusa on 2012-03-25
> **Jimorris said:**
> When I click 'do something else' I get a screen with various options like New partition Table, add,change ,delet,revert and device info e.g. /dev/sda....../dev/sda1 nfs etc

I have no idea what I am supposed to do at this point so any advice and direction much appreciated.


Details of the manual partitioning process can be found at:

[http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/)

The posting includes links to a number of relevant web pages and video tutorials.

---

### Post by clive littlewood on 2012-03-25
Hi

When you get to the partition screen and no option to "Install alongside windows" is shown this usually means that not enough space is available for Ubuntu.

Run the commands asked for above and this will give us a better idea of your partitions.

Clive

---

### Post by Mark Phelps on 2012-03-25
From my experience, the lack of an Alongside option in the installer generally means the installer is unable to create the new partition needed for the installation.

Some common reasons for this:
1) The hard drive already has the maximum number of partitions allocated: 4 Primary, or 3 Primary + 1 Extended
2) The hard drive is formatted with Dynamic Disks -- something the installer does not understand
3) The installer does not under the BIOS scheme in use (GPT or UEFI)

None of these are fixable from inside the installer.

---

### Post by Jimorris on 2012-03-26
> **garvinrick4 said:**
> Run your install cd in Try Ubuntu instead of install.
when boots open a terminal ctrl/alt/t
```
sudo fdisk -l
``` (lower case L)
```
sudo parted -l
``` (lower case L)

Post the output: (copy and paste in your thread)

ctrl/alt/t does not seem to bring up a terminal I had to search for one !!
However here is the result:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df4f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58589054    29294496    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA IC25N030ATCS04-0 (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  30.0GB  30.0GB  primary  ntfs         boot


Error: /dev/fd0: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-03-26
You only have one NTFS primary partition on a 30GB drive. Windows 7 usually wants 30GB, I think XP prefers 20GB but will work with 10GB, but the issue may be how full is your XP partition?

NTFS partition need lots of free space to work well. Often 30% is required, at 20% it starts to slow down and at 10% free you do not have enough room to do much. Ubuntu needs free space also and it hides 5% to make sure you do not crash system.

How much is free?

If you click on sda1, it should auto mount it and this shows mounted partitions use, cd will of course be 100%:

sudo df -h

---

### Post by Jimorris on 2012-03-27
> **centaurusa said:**
> Details of the manual partitioning process can be found at:

[http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/)

The posting includes links to a number of relevant web pages and video tutorials.

I followed these instructions and it now only boots ubuntu.

I guess this is some kind of progress !

---

### Post by GregA on 2012-03-27
Welcome to Ubuntu  . . !

The fastest way to learn Linux, via the Ubuntu family of distributions, is to overwrite Windows as you appear to have done.

Also, since your system has limited resources, you may want to read about installing the most light weight desktop environments, . . . the default "Gnome or Unity" desktops may not be suitable - especially for Linux novices.

If you have less than 2gigs of ram, check into XFCE or LXDE or OpenBox - although there are other light weight desktops.

If you have 2 gigs or more of ram, another option is the KDE4 desktop, which is most like Windows 7 and requires a lower learning curve.

Good luck, and may the odds be ever in your favor!

---

