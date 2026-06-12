---
title: "TIPS Multiboot and partitions"
date: 2009-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by 3Miro on 2009-03-29
This is supposed to be general info and help, for novice users on how to create partitions and multi-boot Linux/other OS. I noticed that it was somewhat common question for people to ask, i.e how to make Linux dual-boot with another OS. After several searches, I did not find a suitable basic tutorial so I decided to make one (I have been dual or triple booting for most of my life so I think I have enough experience to share with novice users)

Every hard drive (HD) could be split into separate partitions. Every operating system OS needs a partition or two to live on. The number of operating systems (OS) that you might multi-boot is only limited by the size of your HD and the number of partitions you have made.

General Info on Linux: 

To operate well, Linux needs at least two partitions (and two is quite enough). Windows has a page file (when it runs out of memory it moves data on the HD), Linux has a page/swap partition. On a computer with a lot of RAM Linux can work well enough without swap, but some features (such as Hibernation, which is very important on Laptops) would be lost. During Linux installation one has to select a partition for "/" and "swap". "/" is the beginning of the file system, it is like "C:" on Windows. The swap partition should be between the size of your RAM and twice that. I would advice, if you have 1GB of RAM or less, make the swap twice your RAM size, if you have more than 2GB you could make the swap the size of the RAM to save some space. The "/" partition should be at least 10GB.

General Info on Windows:
Win XP is fine on one partition, but my advice is to make it at least 15GB. I don't know how much Vista needs, but I imagine it is more.

Above are the minimum requirements to have stable a system running simple web/media/office tasks. In you plan on installing more applications, plan ahead to make sure you allocate enough space.

Some Case Studies:
1. I have windows XP/Vista and I want to try Ubuntu Linux, how do I do that? (I assume you already downloaded and burned the Ubuntu LiveCD) 

First of all, if might want to consider installing it via wibi. That is, Ubuntu would just assume one folder within Windows and upon reboot you will have a choice of Ubuntu vs Windows. Installing Ubuntu that way would work, but Ubuntu itself would be somewhat slower than normal. It is a good way to try Linux with minimal change to your system (you can also uninstall it easily from within Windows).

-OK, what if you want to have Ubuntu in its full power, how do you make it share the HD with Win:

Advice: Backup all important data from the entire HD onto external media (HD/DVD/CD).

The best way probably is to go to Control Panel -> Administrative Tools -> Hardware Manager and then Disk Management within Windows. Most systems already have multiple partitions on their HDs. Select a partition (preferably >10GB) and delete it WARNING: all data on that partition would be lost, you want to make sure you have backed up all your data at lest on the partition in question. Then create two new partitions, one for swap and one for "/". At this point it makes no difference what file system you assign and whether you format them or not.

Then boot from the LiveCD and select Install Ubuntu (or Kubuntu or XUbuntu or whatever).

When you get to the point of asking about the HD and partitions select CUSTOM/MANUAL you do NOT want guided/authomatic or anything of that sort, it may damage windows.

From the custom/manual menu, you will be taken to the gparted, the partition editor. The you will see your HD with all of its partitions. Select the one you created for "/", select file system ext3 (or ext4 for Ubuntu 9.04 and newer) and select mount point "/". Then select the swap partition and mark it as swap file system. Proceed with the install. (Creating the partitions under windows means that you don't have to repartition now, just select the ones you have already made)

On the Advanced options make sure "Install Boot Loader" is selected so that you will be able to choose Windows/Linux on boot.

2. I want to use two versions of Linux, either 32 vs. 64-bit one or 8.10 vs 8.04 for LTS or want to keep the stable 8.* and install the 9.04 beta, how do I do that?

The main difference between this and the windows case is that two Linux installs could share the same swap without any trouble. So you need one swap partition and two "/" partitions for the two systems.

If you already have one Linux installed, use gparted or something similar to create an extra partition for the new "/". Then boot from the second CD and select the already existing swap to be the swap and the new partition for "/".

If you have nothing installed, or you want to wipe out everything already installed (and I mean WIPE OUT EVERYTHING). 
-Boot from the first LiveCD.
-Select CUSTOM/MANUAL partitioning. 
-Delete all partitions.
-Create the partition for this Linux and mark it ex3/4 and mount point "/".
-Create swap partition.
-Create the partition for the other Linux, but do not give it a mount point yet.
-Install with the boot-loader.

To install the second Linux, start from the second LiveCD and from CUSTOM/MANUAL partitions select the proper one for "/" (the one you gave no mount point to). Then install the rest and probably you want to reinstall the boot-loader.

Boot-loader: Ubuntu comes with some nice automated scripts that would detect what kind of OS you have on your PC and make them show up on boot. If you do not install the second boot-loader, you have to manually edit /boot/grub/menu.list. If you already know how to do that, then you probably don't need this tutorial. If not, I suggest you go with the automated scripts (that's what I do in the case of multiple Linux versions).

3. I want more Windows/Linux versions installed. In general how to do that?

Partition your HD whatever way you want by giving all Linux versions one swap to be shared by all Linux and one "/" per Linux version, plus one partition for each windows (at the least that many, you can have more partitions than that). You can use either windows partition system or the one that comes with their install CD, or gparted started from either the LiveCD or within already installed Linux.

Install Windows versions first. Windows is unfriendly towards Linux and will refuse to recognize it as another OS, that is, if you have any Linux installed already, you will be unable to reach back to it. In such case, you will have to boot from a LiveCD and reinstall the Linux boot-loader (just the loader not all of Linux). The way to do that may depend on your system.

4. How do I share data between Windows/Linux?

The default XP and Vista file system is NTFS. By default Linux reads that file system. From Places on the start menu, you should be able to see all of your partitions and access them (you may be asked to enter your password, you can do that and select "remember" so you don't have to do it every time).

The Linux file system is ext3 or ext4 (depending on the Linux version), by default windows cannot read ext2/3/4. One can install software under windows that would allow it to read the data on the Linux partitions, but I have never done that myself.

Probably the easiest way to share data would be to make another partition and (from within windows) format it as NTFS. Then both Linux and Windows would be able to read it. I had such partitions before and used them to store music and pictures and other OS independent files.

Linux could read/write directly into the partition where windows lives, however, one has to be careful. Note that this is true for windows directly writing into the Linux partition. From within Linux, access only OS independent files (such as pictures and music), if you even try to access .dll and other files you could damage windows. Best is to only pick on tings in the windows My Documents folder.

5. I already have Windows/Linus installed, but I don't have any partitions (this or the case if you have the default Ubuntu setting: two partitions and one is mounted as "/" and one as "/home"). Can I resize a partition?

WARNING: back up ALL important data from the ENTIRE HD before you try resizing a partition!!!

I am not sure about the resize capabilities of windows, but gparted generally supports it. A word of caution, it is risky and you may end up loosing ALL of your data. Do backup first. You can start the LiveCD and select try Ubuntu without changes. The run gparted from within.

6. Other advices?

First: backup everything important (you don't want to loose the pictured from your family vacation because of some stupid operating systems).

Other: Make all of your partitions different sizes. Gparted and the windows programs have somewhat different layouts and if you have many partitions (I once had 7 partitions over two HDs) it may be confusing when you are moving from one to the other. If you make partitions have different sizes (even if the difference is 1-2GB) it would be easier to distinguish them. You don't want to install the wrong OS to the wrong partition and end up destroying data.

Other: Plan ahead on how many systems you want to have and how much space you need for each. Games under windows take a lot of HD space. Video files can take a lot of space. In general it is hard to reconfigure the partitions when they are already done. Try to repartition as little as possible.

I hope this is helpful.

---

### Post by Hilko on 2009-10-04
I'd like to add something to this:

If you plan to install three or more operating systems, i highly recommend making a separate GRUB partition.

Furthermore, before you start, i absolutely recommend reading this site and the subpages in there that seem relevant to you. [http://members.iinet.net/~herman546/]("http://members.iinet.net/~herman546/")

This site is the holy grail for anything you need to know about dual booting, multibooting and GRUB. If at some point you have any questions or problems, go back to that site. It has all the answers. Don't forget to bookmark it.

---

### Post by meka4996 on 2009-10-18
[http://ubuntuforums.org/showthread.php?t=1169648](http://ubuntuforums.org/showthread.php?t=1169648)
Moving from Dual Boot to Multi boot [Dedicated GRUB Partition]
my 2 cents ~

---

