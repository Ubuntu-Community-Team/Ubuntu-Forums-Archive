---
title: "Not sure how to properly re-align my hard drive"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Dural on 2012-10-26
I've been using Ubuntu 12.04 as my sole OS for about a week. Before I tried Ubuntu by installing it on a pen drive while using Windows as my primary OS. My laptop is a HP HDX 16 1140-US. The original drive was replaced with a Hitachi Travelstar Z7K500. It could still use the Intel Rapid Storage program but I was not sure whether it needed a RAID setup on it or not when I installed Ubuntu. 

Using Ubuntu has generally gone well, but when I went into the disk utiilty, it said the following:
> WARNING: The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested.

I checked around and found some information in these links:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/#tools](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/#tools)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Here is the list I got from fdisk. It seems that's what I get for using the default install options for Ubuntu. It aligned the partitions by cylinder, but my hard drive is a Hitachi Travelstar Z7K500 which used the Advanced Format. So while the rest of my drive is properly aligned, the extended partition is not. 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00060949

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   972584959   486291456   83  Linux
/dev/sda2       972587006   976771071     2092033    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       972587008   976771071     2092032   82  Linux swap / Solaris

```

I want to repartition my hard drive, but I'm not sure which approach to take. I don't have much data on my drive yet and I wouldn't have much to backup (most of my data is backed up already) but I would prefer to not have to re-install if possible. 

So I have two questions:

a) What would be the best way to re-align my hard drive? I've installed gParted just in case.

b) Do I need to recreate the RAID to be able to properly use my hard drive?

---

### Post by oldfred on 2012-10-26
You do not need to worry. You do not write into the extended partition but the logical partitions inside the extended. So if every primary & logical start on a sector that is divisible by 8 you are ok.

Some of my references are the one's you already posted. 

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

If you really want to repartition and will not be using Windows consider gpt partitioning. Then you do not have extended & logical partitions.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

Some have used the SSD part of the Intel just for Ubuntu as a boot drive as an SSD.
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by Dural on 2012-10-26
What if I'm on a network with Windows computers? Can I still share my files with them if I use GPT instead of MBR?

---

### Post by oldfred on 2012-10-26
Partitioning type is lower level. 

All drives over 2TB, and all new systems with UEFI are using gpt.

I have not heard of any issues but do not know.

---

### Post by Dural on 2012-10-26
I don't have an SSD. My hard drive is a normal hard drive. I know my computer uses Intel Rapid Storage Technology which is different from Smart Response. Smart Response is the technology for hybrid drives and Rapid Storage is for RAIDs. I just want to know if I need to use something like dmraid for my hard drive or should I just leave it alone since I'm only using a single boot system.

---

### Post by oldfred on 2012-10-26
I do not know RAID, but if you have only one drive, you really cannot use RAID. Not sure what Intel is doing then?

---

### Post by sandyd on 2012-10-26
The intel rapid storage thingamajig shows up even if you have only one drive. Have the same thing in my laptop

---

### Post by Dural on 2012-10-28
> **sandyd said:**
> The intel rapid storage thingamajig shows up even if you have only one drive. Have the same thing in my laptop

That's right. I know that when I had Windows 7 there was an icon of a drive which represented Intel RST. It would monitor the health of the drive and provide other information about it. Is there something like that for Linux? I know that I can't use ProtectSmart because there are no Linux drivers for it and I don't think there's a way that I can use a wrapper for the Windows drivers.

---

### Post by oldfred on 2012-10-28
There is smart data in Disk Utility. Click on a drive and on right side is a smart data analysis of drive. All I really know is green is good, but you can run a variety of tests. But some errors are considered ok up to a certain level.

Also command line you can install smartmontools.
smartmontools - lists harddrive detail info
> 
The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks.


[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T)

---

### Post by offgridguy on 2012-10-28
oldfred; I'm not sure how you remember all these web links, but thanks.

---

### Post by oldfred on 2012-10-28
I never could remember anything. And getting old is not helping. I still cannot name all 7 dwarfs much less anything else that is a list of thing. 

But I have pretty good recognition and lots of notes. :)

---

