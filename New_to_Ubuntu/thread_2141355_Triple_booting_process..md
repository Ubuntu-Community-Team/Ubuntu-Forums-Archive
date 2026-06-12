---
title: "Triple booting process."
date: 2013-05-02
forum: New to Ubuntu
---

### Post by malinman100 on 2013-05-02
Okay I need to triple boot a system (With windows 7, Ubuntu and Mint) I am planning on putting windows on a 128 GB SSD and then the two Linux Distro's on my 1 TB hard drive (About 100 GB of it) I was then planning on using the 900 GB as a kinda shared drive between them all.. but is this possible? or do I have to save documents on the specific partitions? Another thing to mention is that NOTHING is installed on these drives yet not even windows. they are brand new.

Okay now that my overall plan has been explained can someone guide me through how I would partition everything and install everything without messing everything up? I know I need to install windows first on the first drive (The SSD) and then after this I'm kinda stuck..

I know that you cant give specific sizes to /boot and everything but I just need to know HOW to set these up so I can decide on sizes then.

Thanks 
-Dan :)

---

### Post by dino99 on 2013-05-02
here is how i'm doing a standard installation : [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

note1: that both the swap partition and the /home partition can be used by all your linux OS; but sharing the /home partition can (rarely) generate unexpected trouble due to the settings saved by one distro and conflicting with the settings saved by an other. Thats said, it is better to set a home folder for each linux installation, and have a huge partition for backing up the data your want to save.

note2: ext4 is the best format nowadays

---

### Post by oldfred on 2013-05-02
I have but do not use XP on an old 160GB drive and have multiple Ubuntu installs on my other drives.

First, is this a new system that has UEFI? 
Makes a big difference on how you install or partition. 
If so you need to be sure to install both systems in UEFI boot mode with gpt partitioning or both systems in BIOS/CSM mode with MBR for Windows. Ubuntu will boot from gpt partitioned drives with BIOS and then would give the flexibility to change later to UEFI if desired. But Windows cannot easily be converted.

You do not get a choice as you install as both systems install based on how you boot them. And Windows only installs with UEFI from flash drive not DVD. So if you boot Windows flash drive installer in UEFI mode it installs in UEFI mode. Similar with Ubuntu if you boot in UEFI mode it installs in UEFI.

You can install each Linux with about 25GB for / (root) including /home. Then link folders in your shared data partition back into /home. I shared my Firefox & Thunderbird profiles in a shared NTFS partition with XP and many Ubuntu installs. I still have not moved it to my shared Linux formatted data partition even though I do not boot my XP anymore.

If you specify if you have UEFI and then whether you want UEFI or BIOS type install we can give more details. 
UEFI is new and the future, but not many know it yet. BIOS is 30 years old on its last legs as it cannot support all the new system features but is well known.

---

### Post by malinman100 on 2013-05-02
Yes I think I have UEFI.

---

### Post by oldfred on 2013-05-02
Just because motherboard has UEFI  it also has CSM.
       Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 

Do you want the new UEFI or the known but very old BIOS? 

Since you will only have Linux on the 1TB drive I might use gpt and create both efi partition for UEFI and bios_grub for BIOS and then you can use either or BIOS now and change to UEFI in the future. It would be difficult to add the efi partition at the start of the drive and convert to gpt in the future if you wanted to change later. But both Windows & Ubuntu have to be BIOS or both UEFI.

My standard suggestion, just in your case create a second / (root)  and very large NTFS for rest of drive. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I partition in advance with gparted, but still have to use Something else or manual install to format and choose which partition to use as /. Also be sure to choose which drive to install grub2's boot loader into.

 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by malinman100 on 2013-05-02
so what do I need? Its this right all on the "same" partition.

/ (Root) ,primary, ext 4
Swap, primary,ext 4
/home, primary, ext 4

---

### Post by oldfred on 2013-05-02
Each of those is a partition. But I do not share a /home between installs as of the potential of conflict. Some do say it works at least for a while.
I only have a small /home folder inside my / (root) and all data in data partitions, both NTFS and Linux formatted.

---

### Post by malinman100 on 2013-05-02
So no /home?

---

### Post by oldfred on 2013-05-02
Not if installing several systems. You can use a shared data partition without issues of settings in /home conflicting.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

