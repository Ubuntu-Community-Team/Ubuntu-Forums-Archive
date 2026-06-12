---
title: "ubuntu 12.04 installer does not recognize drive partitions"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by gobettygo on 2012-07-11
I recently purchased a new HP Pavilion HPE desktop running Windows 7. I am trying to install a dual-boot system with 12.04. However, when I run the LiveCD I only get as far as the "Install" window where you can select the partitions for your drives. On the bottom where it says "device for boot loader installation" I have "/dev/sda" and cannot select any other devices.

All the options to change the drives are greyed out, most likely because there are no drives in the window. I partitioned my largest drive using the tools within Windows, then booted into the CD, but nothing shows up. I then used Gparted to change the new space from unallocated to an /ext2, and still nothing shows up.

The installer does not recognize anything, but when I go into an Ubuntu session and use the disk utility manager I can see the partitions I made. Anything I do has to be done outside of the installer.

I have no files on this new computer, so this is the perfect time to install a parallel OS. I would like avoid completely reinstalling Windows, however. I've been over the forums many times, but all the answers I've found have not worked for me. I also tried flagging the new, empty partition as boot, but that screwed Windows up.

Also, the WUBI installer hits the same point and quits. Any help would be much appreciated!

---

### Post by oldfred on 2012-07-12
Welcome to the forums.

How many partitions do you have? Often Windows computers use all 4 primary partitions and you have to delete one. Also if you created partitions with Windows it may convert from basic to dynamic. If it converted to dynamic that is Windows proprietary and will not work with Ubuntu, It also does not work all the time with Windows.

Post this from liveCD terminal:

sudo fdisk -lu

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by interkin3tic on 2012-07-12
I had a similar issue as OP, I have a samsung laptop.  I was a bit rash and shrank the D partition by 20 gb in windows.    Ubuntu installer doesn't give me the option to install there.

This dynamic vs basic you're talking about, how would I know if it's one or the other, and how would I change it if it is dynamic?

Lastly, is there any way to do this without erasing at least one partition?

---

### Post by puntigamer on 2012-07-12
Try to make some free space, resizing NTFS partitions, and then create your SWAP and root. Don't worry about /dev/sda, if it's your only hard drive (not partition), it should be ok ;)

---

### Post by NikTh on 2012-07-12
Of course the problem must be that HP Laptops come with already 4 primary partitions. 
1)Windows Reserved 
2) Windows files 
3) HP TOOLS
4)HP Recovery. 
So the problem is that Ubuntu installer has not the ability to create another partition.

The solution IS NOT to delete anything. You need all these partition , each for a reason. 
You must "play" a little with Windows Files partition , to transform it Extended and shrink it with a tool "PARTITION MAGIK" . 
I recently encountered same situation with HP and solved it . 
Here is the site and the how to  --> [http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-loaded-Windows-7/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-loaded-Windows-7/td-p/742019)

---

### Post by oldfred on 2012-07-12
While NikTh suggestion will work, I think it is a bit better to move the vendor utilities partition to a logical partition if you want to keep it. Many just delete it and have said that can be downloaded from HP easily as it is small. Others create the vendor image to DVD and do not need the vendor recovery anymore. Most prefer a backup after updates and deleting all the cruft that the vendor has included. The only reason for the vendor recovery if you have good backups is to restore to "new" if you want to sell and the buyer insists on Windows.

Windows only boots from a primary partition. Some have damaged boot partitions, the 100MB hidden partition and then have to repair the main c: drive partition. That can only be bootable/repaired to boot if it is primary.

Windows partition screen will say basic or dynamic or post this from Ubuntu, and it will say SFS.

sudo fdisk -lu

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

You should have a repairCD or liveCD/USB for the current version of every operating system you have installed.

---

### Post by NikTh on 2012-07-12
[COLOR=Red]oldfred[/COLOR]
The idea of create a Repair Cd/dvd of windows its very nice and useful in any sense.
I don't really know if delete the HP-recovery partition or even the Hp-tools partition  affects the warranty of machine. I think its better to ask this. 

He must transform and shrink ONLY the partition with windows files . Not 100MB reserved partition , not anything else. Windows boot from 100MB reserved partition . This partition will not tampered. Its primary and will remain primary.

---

### Post by gobettygo on 2012-07-12
Here is the output from fdisk -lu. The fourth partition is what I shrank from the original Windows C: drive (within Windows) and then used GParted within the live session to allocate it. I was hoping the installer would recognize it and install from there, but no dice.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x410adf38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   965111807   482452480    7  HPFS/NTFS/exFAT
/dev/sda3      1917227008  1953122303    17947648    7  HPFS/NTFS/exFAT
/dev/sda4       965111808  1917227007   476057600   83  Linux

Partition table entries are not in disk order

Edit #2: I have attached a screenshot of the installer and my (lack of) options for the drives. It happens every time, and at this point I would not even be able to install at all, let alone dual boot.

---

### Post by oldfred on 2012-07-12
You have sda4 as a primary partition in Linux format. If you have no data in it delete it and then the installer should  work. You need a minimum of two partitions normally one / (root) and the other swap. But both and any more you may want can all be logical partitions in an extended partition.

If you want to use Something else then you can use gparted to create partitions and then choose which partition is /, which is swap and then you can also create a separate /home or other partitions.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by gobettygo on 2012-07-12
Should I delete the Linux partition in Windows or through GParted? 

Initially, before I split my drive, I intended to just partition the drives through the installer, but as I posted above I can't even get that far. I can't select any options or go forward with the installation.

---

### Post by oldfred on 2012-07-12
Only use Windows tools on Windows to shrink it. Use Linux tools for Linux as a general way to do things.

Use gparted to delete sda4 the Linux formated partition if you have no data in it.

---

### Post by NikTh on 2012-07-12
> **gobettygo said:**
> Here is the output from fdisk -lu. The fourth partition is what I shrank from the original Windows C: drive (within Windows) and then used GParted within the live session to allocate it. I was hoping the installer would recognize it and install from there, but no dice.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x410adf38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   965111807   482452480    7  HPFS/NTFS/exFAT
/dev/sda3      1917227008  1953122303    17947648    7  HPFS/NTFS/exFAT
/dev/sda4       965111808  1917227007   476057600   83  Linux

Partition table entries are not in disk order
Hmm.. then i must understood wrong from your first post. You have already create a linux partition so you must be able to install Ubuntu in this partition. 
Try to use gparted to set the partition as unallocated space . No file system.(Delete) Then Ubuntu installer must recognize the partition as Free Space. Tick it and format to "etx4 with journal" and mount it to / (root)

---

### Post by jim_24601 on 2012-07-13
I think we are talking at cross-purposes here. The OP is concerned that the installer wishes to install the *boot loader* on /dev/sda rather than a partition. But this is perfectly normal. You need to install the boot loader to the boot sector of the hard disc, not to a partition, because that's where the BIOS will look. (Otherwise the computer would just load the existing Windows boot loader and you woudln't be able to boot your new Ubuntu system.)

---

### Post by bmtahimic on 2012-07-14
First of all I apologize for being such a noob. I have been running Win7 Ultimate 32bit on my lenovo g450 notebook where the HD is partitioned into C & D drive. I installed/dual booted and installed Ubuntu 12.04 in the drive. Ubuntu installed with no problems, I have 262 GB Filesystem showing up when I open File system, I can open all my files and folders in the C drive but I cannot for the life of me find the files that I can see in my D drive when I used Windows 7. Did installing Ubuntu on the D drive wipe all thats in there? I have not tried rebooting and selecting win 7 as my OS since I am still downloading something while logged into Ubuntu. Any input is appreciated. Thanks in advance!

---

### Post by oldfred on 2012-07-14
Repost the sudo fdisk -lu or the much more complete Boot-Info to see entire system configuration.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary - uses standard bootinfoscript but adds some extra info
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You can install the Boot-Repair script into your install, run from Ubuntu liveCD (but have to redownload each time you reboot), or download a full liveUSB with it included.

---

