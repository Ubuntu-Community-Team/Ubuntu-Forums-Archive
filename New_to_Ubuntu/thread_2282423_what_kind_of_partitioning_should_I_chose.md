---
title: "what kind of partitioning should I chose"
date: 2015-06-14
forum: New to Ubuntu
---

### Post by Xpdin on 2015-06-14
[COLOR=#111111][FONT=Ubuntu]I would like to make a new installation of Lubuntu Core I will use only Lubuntu Core on this machine. I use a [HP 6820s]("http://www.cnet.com/products/hp-compaq-6820s-17-core-2-duo-t5870-vista-business-xp-pro-downgrade-2-gb-ram-250-gb-hdd/specs/")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I will have very few files on HDD, some poor quality movies and some documents.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I would like to partition the HDD like this:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
HDD 250 GB:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
20GB - ext4 - / - for the operating system 
4GB - swap 
The rest of 220 GB on 2 equal partitions of ext4.
[/FONT][/COLOR]

[LIST=1]
[*]Is this the best chosen HDD partitioning for speed?
[*]Is ext4 the best solution for speed for my hardware configuration and my files using?
[*]If sometimes I will use some files from Windows should I create a FAT32 partition too?
[*]Will the FAT32 partition make the system slower? If yes, it will help in any way if it will be of only a few GB?
[/LIST]
[COLOR=#111111][FONT=Ubuntu]
Thanks.[/FONT][/COLOR]

---

### Post by UltimateCat on 2015-06-14
Hi:

A 4 GB swap is a tad much. Maybe make your swap partition 1 to 2 GB.....that's plenty.

I prefer EXT 4 for my journaling file system (partition for the os) but members use a EXT 3 as well.

You may want to list more information about your pc by posting the output of:
```
lspci

```
That way other members will know what kind of hardware you have.

> Will the FAT32 partition make the system slower? If yes, it will help in any way if it will be of only a few GB?


Wait for a member with more experience to answer that; I'm not sure. I haven't ran Windows in about 4 years and have forgotten.

-:-You should be able to mount your Windows files from your Lubuntu distribution.-:-

[http://tldp.org/HOWTO/Partition/partition-types.html](http://tldp.org/HOWTO/Partition/partition-types.html)
[http://www.computerhope.com/issues/ch000452.htm](http://www.computerhope.com/issues/ch000452.htm)
[http://www.maketecheasier.com/convert-files-from-linux-format-windows/](http://www.maketecheasier.com/convert-files-from-linux-format-windows/)

---

### Post by nerdtron on 2015-06-14
> 
3. If sometimes I will use some files from Windows should I create a FAT32 partition too?
4. Will the FAT32 partition make the system slower? If yes, it will help in any way if it will be of only a few GB? 

What do you mean "use some files from windows"? Are you going to dual boot? or just share some files with windows computers?
Linux can read and write NTFS partitions just fine if you that is what you are asking. NTFS support is stable and I haven't ran into problems. As for speed, there is not much noticeable difference unless you run benchmarks of course, non-native filesystems like NTFS can be slower.

---

### Post by Bucky Ball on 2015-06-14
If you want to share data with Windows create an NTFS partition, not FAT. FAT has limitations and is old.

The rest is fine. For Ubuntu, basically:

/ = ext4, 20-25Gb fine,
/swap = 2Gb, unless you hibernate and then same size as your installed RAM ('swapspace' will be chosen for the filesystem).

If you don't hibernate, you don't need a 4Gb swap. A separate /home is optional. Has its advantages.

---

### Post by Xpdin on 2015-06-14
Thank you very much for your replies.
Excuse me, but I would like to remind you that I am beginner...

> **UltimateCat said:**
> Hi:

A 4 GB swap is a tad much. Maybe make your swap partition 1 to 2 GB.....that's plenty.

Sorry, I thought the swap partition should be 1/3 or 2 times more than the RAM memory, the system has 2 GB of RAM Memory. I use "Suspend" for the system.

> **UltimateCat said:**
> 
I prefer EXT 4 for my journaling file system (partition for the os) but members use a EXT 3 as well.

Can someone tell if there are speed differences between EXT 4 and EXT 3

> **UltimateCat said:**
> 
You may want to list more information about your pc by posting the output of:
```
lspci

```
That way other members will know what kind of hardware you have.

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516/M62-S [Mobility Radeon X1350]
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)

```

> **Bucky Ball said:**
> 
The rest is fine. For Ubuntu, basically:

/ = ext4, 20-25Gb fine,
/swap = 2Gb, unless you hibernate and then same size as your installed RAM ('swapspace' will be chosen for the filesystem).

If you don't hibernate, you don't need a 4Gb swap. A separate /home is optional. Has its advantages.

The system has 2 GB RAM memory, I use only "Suspend" never "Hibernate". In this situation do you still consider that would be enough 2 Gb for the swap partition?

> **Bucky Ball said:**
> If you want to share data with Windows create an NTFS partition, not FAT. FAT has limitations and is old.

> **nerdtron said:**
> What do you mean "use some files from windows"? Are you going to dual boot? or just share some files with windows computers?
Linux can read and write NTFS partitions just fine if you that is what you are asking. NTFS support is stable and I haven't ran into problems. As for speed, there is not much noticeable difference unless you run benchmarks of course, non-native filesystems like NTFS can be slower.

I am not going to run benchmarks...

I will number the questions to be easier for you to answer... 

1. For the moment I am not going to share data with Windows, but in case of it will happen, the best way is to have a little NTFS partition on my HDD? 

2. I am a home user, maybe I could take those info which I should share with Windows on a USB Stick, and don't need to share the data with a Windows anymore? 

3. Or are there any other mandatory situations when there is no other ways, and I must share data with Windows?

4. Sorry, but when I installed Lubuntu, I don't remember to be any NTFS option for the partitions format, only those ext1,2,3 FAT32,16 etc, but not NTFS.
Should it be there with the others, and called NTFS as well ? 

Thank you very much.

---

### Post by dino99 on 2015-06-14
about partitionning: remember the 4 primary limitation; so better to create an 'extended one in which you create the other needed ones. A 4 gb swap partition is safe, and be never fully used, all depends of the apps ran: like compiling, programming, many browser tabs opened, ...
Creating a /home separate partition is a good choice

---

### Post by Mark Phelps on 2015-06-14
You only need an NTFS partition if you are going to share data with Windows on the same PC as you have Lubuntu installed; otherwise, using a USB stick is fine.

There was no NTFS option during install because Lubuntu needs a Linux filesystem for installation.  GParted will let you format NTFS partitions.

---

### Post by LastDino on 2015-06-14
[B]Assuming I'm understanding you correctly;

1. For the moment I am not going to share data with Windows, but in case  of it will happen, the best way is to have a little NTFS partition on  my HDD? [/B]
You need NTFS *only* if you&#8217;re actually going to have a Windows OS on the system which is going to use *that particular NTFS partition* as a data/media partition. Linux can read Windows files fine even if you transfer them from pen-drive from some other Windows Machine. On that note: Windows can't read files which are stored on Linux native partition types like (ext3 or ext4), however, you wont have problem reading those files on other windows machine as long as you're transferring them on Pen-drive/SSD which is in WIndows partition types (i.e FAT 32 OR NTFS). To which Linux can transfer files if needed as it can read it.

TL;DR If you're only going to use Linux on this particular system, you don't need NTFS or any windows partition for that matter.


** 2. I am a home user, maybe I could take those info which I should share  with Windows on a USB Stick, and don't need to share the data with a  Windows anymore? **

You don't need a shared partition if you don't have a Windows installed on the same machine, you can store those files on Linux native types too. Given you use pen-drive/ssd formatted in a windows partition style which is readable by both Linux and Windows. BUT if you're planning to dual boot, make an NTFS partition. 

I usually don't suggest separate /home but you can have one on your Linux system just in case your Lubuntu crashes and you need to re-install. That way your user settings as well data will be safe as it is stored on /home. 

** 3. Or are there any other mandatory situations when there is no other ways, and I must share data with Windows?**
It is completely up to you, if your machine is running both WIndows and Linux, you might want to share data through NTFS, but if you've Windows installed already, its partition is already readable by Linux.
[B]
4. Sorry, but when I installed Lubuntu, I don't remember to be any NTFS  option for the partitions format, only those ext1,2,3 FAT32,16 etc, but  not NTFS.
Should it be there with the others, and called NTFS as well? [/B]

Gparted will allow you to create NTFS.

---

### Post by Bucky Ball on 2015-06-14
2Gb for /swap is all you need.

As mentioned, four partition limit unless you are using UEFI mode. Do you have Windows and the data you've created with it on one big partition? If not, do you have data stored already on another partition that is not EXT*? You can simply use that if so as it is already probably NTFS. If you look in Gparted on the Live boot (or install and launch if on an installed Ubuntu) you can have a look at the way your drive is set up and what filesystems are being used. A screenshot of Gparted attached to your next post here would be handy.

1 Little NTFS partition called /share or something like that is fine. Just save any files you need to share to that (or you can create a big NTFS data partition and tell your Win to see that as Documents or whatever you need it to and create symlinks in the /home directory of Ubuntu to link to the folders in there (i.e. Documents, Videos, Music, etc.)). Unfortunately, or fortunately, depending on how you look at it, there are a few ways to go about it. Make a solid plan regarding how you are going to go about it, as you're trying to do, then launch. :)

2 USB for transferring data will work fine. Remember, the partitions are either ext or ntfs, NOT the files. ;)

3 There are no situations where this is a necessity unless you create one. The systems have nothing whatever to do with each other. Win and Ubuntu are on separate partitions and you boot one or the other. The only connection is that Ubuntu knows Win is there and Win knows something's there.

4  See 1. Open Gparted and report back.

Hope that is of some help.

---

### Post by dino99 on 2015-06-14
Let do things simple :p

- old hardware means no 'uefi' here; so forget posts that complicate explanations
- home user with a windows installation and a ubuntu one project: first clean/chkdsk windows if needed, and shrink unused windows space if needed. Then check how many 'primary' partition already exist (max<=4); ubuntu can be installed an 'extended' one, with a / (root) ext4 & 15 gb, a swap 2>4 gb, and /home ext4 for your data é settings. Create the partitions with gparted live, then you choose 'something else' installer option to select the previous created partitions.
- ubuntu (linux) directly understand the ntfs partition (via its ntfs-3g default installed driver) so again no needs complication here.
- when the installer ask for the bootloader (grub2) then install it on /dev/sda
- when finished, remove the cd/usb installtion device, and reboot

voila ):P

---

### Post by vasa1 on 2015-06-14
> **dino99 said:**
> Let do things simple :p
...
- home user with a windows installation and a ubuntu one project: first clean/chkdsk windows if needed, and shrink unused windows space if needed. ...
+1.

I would include a defrag step to start things off as well. Then, after the volume shrinking, some people recommend two (!) reboots just to get Windows to properly register the "shrinking".

---

### Post by Steve_Horan on 2015-06-14
Or play with BTRFS. It is the future. ):P

---

### Post by UltimateCat on 2015-06-15
> **Mark Phelps said:**
> You only need an NTFS partition if you are going to share data with Windows on the same PC as you have Lubuntu installed; otherwise, using a USB stick is fine.

There was no NTFS option during install because Lubuntu needs a Linux filesystem for installation.  GParted will let you format NTFS partitions.

Thanks for confirming that; I wasn't sure.

---

