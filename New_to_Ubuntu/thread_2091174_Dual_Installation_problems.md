---
title: "Dual Installation problems"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by spaniel on 2012-12-04
I am absolute beginner and have been helped by this forum with my first Ubuntu installation. I havetried to have a dual operating system along with Vista Ultimate,
but if I install Ubuntu first, then after Vista is installed Ubuntu gets wiped out. I tried installing Vista first, by creating partitions using Easeus, on the 500Gb hard drive.
I've got a dual boot system but Ubuntu is a folder in Vista's C/Program Files, and Ubuntu logs me on as a guest, and after I log out of Ubuntu it erases the work saved.
How to install Ubuntu as an operating system in its own right. Thanks,

---

### Post by oldfred on 2012-12-04
Welcome to the forums.

I would create sda1 or first partition (so it is a primary partition)  NTFS with the boot flag of a size you want for Vista. Probably no less than 30GB. I would also create another NTFS partition for shared data. 

Then using Linux tools like gparted from liveDVD or USB flash installer create an extended partition for the rest of the drive. Inside the extended partition create partitions for Linux including / (root), /home and swap. Then you can use manual install or something else to choose which partition is / and /home. Swap is normally automatically found if created in advance.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
    [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
       [https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
            Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


       
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Mark Phelps on 2012-12-04
> **spaniel said:**
> I am absolute beginner and have been helped by this forum with my first Ubuntu installation. I havetried to have a dual operating system along with Vista Ultimate,
but if I install Ubuntu first, then after Vista is installed Ubuntu gets wiped out. 
Actually, it probably does NOT get wiped out -- unless you allow Vista to take over the entire disk.  What most likely happens is that Vista overwrites the MBR and you don't see a boot selection for Ubuntu anymore.

> I tried installing Vista first, by creating partitions using Easeus, on the 500Gb hard drive.
I've got a dual boot system but Ubuntu is a folder in Vista's C/Program Files, and Ubuntu logs me on as a guest, and after I log out of Ubuntu it erases the work saved.
Don't understand this.  IF you installed Ubuntu from INSIDE Vista, then it used Wubi and created a virtual filesystem inside the Vista partition -- but it should still start OK and work like a regular installation.
> How to install Ubuntu as an operating system in its own right. Thanks,

If you have Vista installed, and want to install Ubuntu to its own partition as a dual-boot setup, then read through the details below:

If Vista came preinstalled on your PC, it's likely the PC builder already used the maximum of 4 Primary partitions -- in which case, you can't create another one.

To see the disk partitions, boot into Vista and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Vista Disk Management utility to shrink the Vista OS partition to make room on the drive. Vista, like Win7, is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Vista unbootable.

And, after you create some free space, do NOT format it using the Vista Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

