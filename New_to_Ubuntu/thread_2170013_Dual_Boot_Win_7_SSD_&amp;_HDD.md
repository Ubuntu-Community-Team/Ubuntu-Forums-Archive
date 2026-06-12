---
title: "Dual Boot Win 7 SSD &amp; HDD"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by Earl_Rig on 2013-08-24
I just bought a new computer with Windows 7 on the 120 GB SSD.  The computer also has a 2 TB HDD that I intend to use for data.  I have been using Ubuntu for over a year on the old computer.  I installed it (maybe version 10~) alongside an existing XP installation, which worked just fine.  I would like to now install Ubuntu 12.04 alongside this new Win 7 installation and have them share the SSD.  I will then point both Windows and Ubuntu to the other drive for data.  I did a search on doing this and found a lot of very detailed conflicting information.  I've read through a lot of information for hours, and what I need right now is some advice directed to me for my situation, which is as follows:

System:
ASRock Z87 Mobo
I5-4670 3.4 GHZ processor
8GB RAM
Primary Drive - 128 GB SSD
Data Drive - 2 TB SATA III HDD

Uses:
Windows 7 - General family use, basically only for programs that don't run in Linux.  Only game I play currently is Age of Conan MMO (most games played on Xbox)
Ubuntu 12.04 - General family use, main media computer

I use Windows only when I have to at this point, and have even got the other members of the family used to Linux.  I did the earlier dual boot on the old computer without any complications, partitioning the drive during the install process when prompted.  Knowing that Windows tends to eat up more space, I allocated 2/3rds of the drive to it.  

For this installation, I made a flash drive to install 12.04, and I was thinking I would just put it in and partition the drive when prompted, allocating ~80 GB to the windows partition and ~40 GB to the Ubuntu partition, and then making whatever changes I need to within each operating system to point to the data drive.  Am I oversimplifying or missing something?  Do I need to partition the data drive as well?

Thanks in advance.

---

### Post by oldfred on 2013-08-24
The Z87 is the new UEFI based motherboard. But Windows may be installed in CSM/Legacy/BIOS mode. We need to know which mode Windows is installed in to give good info.
Windows only boots from gpt partitioned drives with UEFI. Ubuntu can boot from a gpt partitioned drive with either UEFI or BIOS. Both systems only boot in BIOS mode from MBR(msdos) partitioned drives.
And many boot Ubuntu in wrong mode and then cannot easily dual boot as Ubuntu installer boots with either UEFI or BIOS and how you boot from UEFI menu is how it installs.

Post this from live mode terminal, and we can see how you are partitioned, which will give an idea of how to install.

sudo parted -l

---

### Post by Earl_Rig on 2013-08-30
Can't do that - I don't have linux on this computer.  Is there another way to get the information?

---

### Post by Earl_Rig on 2013-08-30
I used the Windows 7 disk management tool, which showed the partitions on Disk 0 (the SSD) as:
-System Reserved, 100 MB NTFS Healthy(System, Active,...)
-C: 119.14 GB NTFS Healthy (Boot, Page File, Crash Dump, Primary Partition)

The spinning platters disk is Disk 1
-1863.01 GB NTFS Healthy (Primary Partition)

Does that help?

---

### Post by Earl_Rig on 2013-08-30
Sorry for the multiple posts, but I found it now.  Both the SSD and the HDD are Master Boot Record partition style.

---

### Post by oldfred on 2013-08-30
Since you are BIOS with MBR partitions you have the 4 primary partition limit. But Ubuntu runs from logical partitions without issue, so you just need one primary to make as the extended partition.

If you create partitions before installing Windows you can install it into one primary NTFS formatted partition with the boot flag. If you have Windows installed, use Windows to shrink the NTFS partition and reboot so it can run chkdsk and fix itself to its new size.  Also create a Windows 7 repairCD or flash drive.

Ubuntu's default install is just / (root) & swap and that will work if you are using another drive for data. I prefer to have an operating system on every drive, but use my SSD as my main boot drive. I have two / partitions of 27GB on my 64GB SSD (current & future). And I use about 9GB of the 27GB, but am aggressive about moving/keeping data on data partitions. I used to have a lot of data on a NTFS shared with XP partition, but now do not use XP and all new data is in a Linux formatted data partition on my hard drives. But I also have an Ubuntu install on each data drive. 

While I often suggest the separate /home for new users as then it is easier to reinstall as all data and user configuration files are not overwritten with a new / if you mount and DO NOT reformat on new install. But if keeping all data in other partitions it is not as necessary, but you do need to regularly backup /home in either case so you can restore user settings (and data if not separate) easily.

When you install Ubuntu it will automatically install its boot loader to sda. If that is the SSD it should be ok. If not you have to use Something Else and use manual partitioning. On the partitioning screen is the combo box with the choice of which drive's MBR to install grub2's boot loader into.

Some examples.
 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

 Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

