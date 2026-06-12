---
title: "Installing Ubuntu"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by DaveyH on 2013-05-10
Can I install Ubuntu on a separate hard drive from the Windows drive?

My main C: drive is 1 TB, and holds Windows XP.  The 2nd HD is D: and is 250GB, used for data (mostly video files). I would like to install Ubuntu on the D: drive, keeping it separate from Windows. (I would transfer the data to another drive first, of course).

Which option would I choose in the installation?  Will "Alongside" try to re-partition C: drive? Would "Replace Existing System" erase Windows on C:? 

How do I specify D: drive?  Or is there another method to use?

---

### Post by oldfred on 2013-05-10
With two drives you just about have to use manual install. That is the only choice that lets you choose which drive's MBR to install grub2's boot loader into. And you want grub on the Ubuntu drive and BIOS set to boot the Ubuntu drive as it will let you boot Ubuntu or Windows.

Linux will see your d: as sdb and each partition you create as sdb1, sdb2 etc. The Windows is the on drive sda. Sometimes BIOS changes drive order so you will have to pay attention to which is which. 

How is sda partitioned? if you just have one large NTFS partition you may want to consider splitting it. If dual booting best not to write directly into a Windows system partition, you can set it read only. And then use a NTFS shared data partition for most data and all data you might want to share.

You can install with just / (root) and swap but generally better to also use /home. A few systems do have issues booting beyond 100GB on a drive so if you create a 25GB / at beginning of drive then you will not have any issues.

Some examples are older but the install process is really just the same.
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

I prefer to partition in advance with gparted from live installer DVD or flash or a separate Parted Magic or Gparted liveCD.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.: Click on partition, change, use as ext4, check format, mount as / (root). Same for /home.
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by nsync on 2013-05-11
create a new partition, to do that you have to login to windows and you might have a option to create a new partition. then insert the media containing ubuntu setup and proceed to installation.. - i dont know if this works.

---

### Post by 3rdalbum on 2013-05-11
When the Ubuntu installer starts up, you will be given the option to erase the second hard disk and install Ubuntu to it. You could also use the "something else" option in the installer to manually do your own partitioning of that hard drive.

---

### Post by KARNVORbeefRAGE on 2013-05-11
You might also need to set up that HDD in your BIOS as a boot option since it was previously only used for storage ==> I have never dual booted with two hard drives so you might want to double check this to be sure.

---

### Post by col48 on 2013-05-11
re post #5

I've recently installed a fresh Ubuntu on a second HDD, previously just used for backup data, without giving any thought to adjusting BIOS and the installation did it for me.

(I can't speak for Ubuntu/Windows dual boot, though)

---

