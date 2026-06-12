---
title: "How To Access RAID Disks From Another Device?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by kindastuck on 2012-05-17
I have a faulty NAS which has been running RAID 1. I need to extract the data from the disks (it is the NAS device itself that has failed, not the disks). I removed the disks and put them into a PC which I then booted up with Ubuntu 12.04 LiveCD. It can see the disks (through disk utility) but will not start the RAID array. The error message simply says "not enough components available to start the RAID array".

I'm a Ubuntu newbie and don't know which direction to turn in. Can somebody point me in the right direction to accessing this data please?

Many thanks!

---

### Post by Bushflyr on 2012-05-17
First thing is: What NAS? If it uses a hardware RAID controller you could have problems.

---

### Post by kindastuck on 2012-05-18
> **Bushflyr said:**
> First thing is: What NAS? If it uses a hardware RAID controller you could have problems.

It is an Iomega ix2. The Iomega people have suggested that accessing the data is possible (but without explaining how :-))

---

### Post by steeldriver on 2012-05-18
does the LiveCD system include the mdadm package? I don't think the regular install does

what does sudo fdisk -l see? does it at least identify the partition type?

is there anything like /dev/md0 or /dev/md1 in /dev?

if there is you could start by at least grabbing mdadm and then trying 

```
$ mdadm --detail /dev/mdX
```(where X is the number of the md block device) although you might need a reboot after adding the mdadm tool to get it to detect - might work if you use a LiveUSB with persistence - if not you will need to actually install a system somewhere

sorry, I'm pretty much a RAID n00b too

---

### Post by kindastuck on 2012-05-18
> **steeldriver said:**
> does the LiveCD system include the mdadm package? I don't think the regular install does

what does sudo fdisk -l see? does it at least identify the partition type?

is there anything like /dev/md0 or /dev/md1 in /dev?

if there is you could start by at least grabbing mdadm and then trying 

```
$ mdadm --detail /dev/mdX
```(where X is the number of the md block device) although you might need a reboot after adding the mdadm tool to get it to detect - might work if you use a LiveUSB with persistence - if not you will need to actually install a system somewhere

sorry, I'm pretty much a RAID n00b too

Hi Steeldriver,

Thanks for getting back to me. You have moved me forwards....

The disk utility tells me that each disk contains two "RAID Components". In each case, the first one is 1GB and the second one is 999GB. The "device" names are /dev/sda1, /dev/sda2, /dev/sdb1 and /dev/sdb2.

I ran "sudo fdisk -l /dev/sda2" and it told me:

Disk /dev/sda2: 999.2GB, 999160274432 bytes
255 heads, 63 sectors/track, 121474 cylinders, total 1951484911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimal/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda2 doesn't contain a valid partition table

mdadm was not installed so I installed it. I then ran "sudo mdadm --detail /dev/sda2" and got the error message "mdadm: /dev/sda2 does not appear to be an md device".

Does that mean that this is a "sd" device (as it is sda2?). Whatever "sd" might mean .... ? (I got the same error on /dev/sda1).

---

### Post by kindastuck on 2012-05-18
I've just run "sudo fdisk -l" again and it has given a different result. I'm not sure whether that is because I have mdadm installed for for some of the other things I have been trying. Anyway, it tells me ....

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ecea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     2040254     1020127   83  Linux
/dev/sda2         2040257  1953525167   975742455+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b6f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     2040254     1020127   83  Linux
/dev/sdb2         2040257  1953525167   975742455+  83  Linux

Does that help ????

---

### Post by steeldriver on 2012-05-18
Things like /dev/sda1, /dev/sdb2 are the regular block devices, your RAID array will get constructed out of (some of) those and a /dev/md0 or /dev/md1 or whatever will magically appear - running "mdadm --detail" on the underlying /dev/sdXx device won't work

Likely your /dev/sda1 and /dev/sdb1 are the system partitions of the NAS itself and /dev/sda2 and /dev/sdb2 are the RAID

Here are the relevant bits of the fdisk -l for my box to show how it should look:

```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   83  Linux
Partition 1 does not start on physical sector boundary.
/dev/sda2          112455  3907029167  1953458356+  fd  Linux raid autodetect
Partition 2 does not start on physical sector boundary.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      112454       56196   83  Linux
Partition 1 does not start on physical sector boundary.
/dev/sdb2          112455  3907029167  1953458356+  fd  Linux raid autodetect
Partition 2 does not start on physical sector boundary.

Disk /dev/md1: 2000.3 GB, 2000340168704 bytes
2 heads, 4 sectors/track, 488364299 cylinders, total 3906914392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table


```Notice that my /dev/sda2 and /dev/sdb2 are marked as partition type 'fd Linux raid autodetect' whereas your equivalent partitions are plain type '83 Linux'. EITHER that means it's not Linux software RAID in which case like Bushflyr said you are likely out of luck OR it means it couldn't auto-detect because mdadm wasn't installed at boot time.

You *may* be able to force mdadm to detect AFTER boot but that's beyond my expertise - I don't want to suggest something that might corrupt your data.  EDIT: it should be quite safe to at least try:

```
 sudo mdadm --examine /dev/sda2
```

```
 sudo mdadm --examine /dev/sdb2
```

which will tell you if mdadm can detect a RAID superblock on either of the candidate partitions (I just did it on my running system and nothing bad happened).

Hope this helps

---

### Post by Bushflyr on 2012-05-18
I'm pretty new too, but [THIS BLOG]("http://planetkris.com/2010/11/ix2-nas-drive-failure/") would indicate that it's a mdadm RAID.

Are you 100% sure that the hardware has failed? If you've tried power cycling it a few times with no luck you could try reassembling the RAID. I've been able to rebuild my RAID with no data loss by running:
```
sudo mdadm --assemble --scan
```

I'm not 100% sure how safe it its for your data, but I don't think it will hut anything.

Also, more (tangential) info [HERE]("http://ubuntuforums.org/showthread.php?t=1691972").

---

### Post by kindastuck on 2012-05-19
Hi Steeldriver,

Thanks for that. Yes, I see the difference.

Running sudo mdadm --examine /dev/sdX2 gives me:

```

/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 835b0566:a6ec46fd:dcb0858b:93e1599d
  Creation Time : Fri Mar 27 07:25:20 2009
     Raid Level : raid1
  Used Dev Size : 975742336 (930.54 GiB 999.16 GB)
     Array Size : 975742336 (930.54 GiB 999.16 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Wed May 16 10:26:52 2012
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 17fa6f04 - correct
         Events : 2533112


      Number   Major   Minor   RaidDevice State
this     2       8       18        2      spare   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       0        0        1      faulty removed
   2     2       8       18        2      spare   /dev/sdb2
```

and

```

/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 835b0566:a6ec46fd:dcb0858b:93e1599d
  Creation Time : Fri Mar 27 07:25:20 2009
     Raid Level : raid1
  Used Dev Size : 975742336 (930.54 GiB 999.16 GB)
     Array Size : 975742336 (930.54 GiB 999.16 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Wed May 16 09:10:18 2012
          State : active
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 17d34214 - correct
         Events : 2503425


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       0        0        1      faulty removed
   2     2       8       18        2      spare   /dev/sdb2
```

I think the table at the end is trying to tell me something useful but I am unsure how to translate it.

---

### Post by kindastuck on 2012-05-19
Hi Bushflyr,

Thanks for getting back to me. I think I'm getting somewhere (or at least, I think you guys are getting me somewhere!! :-))

I read through those links you suggested. Yes, the NAS is dead :-( I power-cycled it many times. Looking at the SMART data, one disk was classified as "disk failure is imminent" so I also tried returning the better disk to the NAS with a new disk but it didn't want to play.

I ran the sudo --assemble --scan command and got the following response:

```

mdadm: /dev/md0 has been started with 1 drive (out of 2).
mdadm: /dev/md1 assembled from 0 drives and 1 spare - not enough to start the array.
```Disk utility has now changed what it says under Multi-Disk Devices. It previously simply showed "Array". It now has 3 entries:

RAID Array /dev/md1 (inactive)
RAID-1 Array
1.0 GB RAID-1 Array

Clicking on the first shows a state of "not running, partially assembled" and nothing eles.

Clicking on the second one tells me a few more things:
 - Level = Mirror(RAID-1)
 - Metadata Version = 0.90.0
 - State = Not runnning
 - Components = 2
 - there is also a "Start RAID Array" button shown here (I have not clicked it)

The third one tells me even more:
 - Level = Mirror(RAID-1)
 - Metadata version = 0.90.0
 - Partitioning = Not partitioned
 - State = DEGRADED
 - Capacity = 1.0GB(1,044,512,768 bytes)
 - Action = Idle
 - Components = 2
 - it then has 5 buttons (not clicked any of them!):
  - Stop RAID Array
  - Check Array
  - Benchmark
  - Format/Erase RAID Array
  - Edit components
 - It shows the Volumes as "1.0 GB ext2"
 - Then I am guessing it shows info about this volume:
  - Usage = Filesystem
  - Device = /dev/md0
  - Capacity = 1.0GB(1,044,512,768 bytes)
  - Type = EXT2(version 1.0)
  - Mount point: Not mounted
 - Then it shows 4 buttons (again, not clicked):
  - Mount volume
  - Check filesystem
  - Format volume
  - Edit filesystem label

I am guessing that I can try mounting this volume but maybe I need to do something first?

Many thanks!!

---

### Post by steeldriver on 2012-05-19
OK well that all looks very encouraging - my version is 1.2 so the "--examine" looks a bit different, but the important thing is it is correctly detecting the RAID partition type.

Was the array resyncing to a spare drive when the NAS died by any chance? It looks like it's ignoring the 'active' device and trying to assemble from the 'spare' and another (missing) device.

It worries me a bit that it seems to have assembled TWO arrays - my guess is it put the active device in md0 and tried to make another array in md1 out of the spare. Let's try

```
sudo mdadm --detail /dev/md0
```

```
sudo mdadm --detail /dev/md1
```

and try to figure it out. We may have to pull both apart and re-assemble giving it the partitions explicitly instead of using --scan. Or maybe we can remove the spare from md1 and add it back to md0.

---

### Post by kindastuck on 2012-05-21
Hi Steeldriver,

ok, i'm a dope! I didn't realise that there was a page 2 to this message so I didn't see your reply until now! Duh!

I turned off the PC and restarted it and now (of course!) it is saying something different to me. When I run "sudo mdadm --assemble --scan" it tells me:

```
mdadm: /dev/md0 has been started with 1 drive (out of 2).
mdadm: failed to add /dev/sdb2 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda2 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.
mdadm: failed to add /dev/sdb2 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda2 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.
```

running "sudo mdadm --detail /dev/mdX" tells me:

```
/dev/md0:
        Version : 0.90
  Creation Time : Fri Mar 27 06:32:58 2009
     Raid Level : raid1
     Array Size : 1020032 (996.29 MiB 1044.51 MB)
  Used Dev Size : 1020032 (996.29 MiB 1044.51 MB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 20 16:44:28 2012
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : f4bbf855:b2d100c6:39ef04d2:f61103c6
         Events : 0.1473386

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        1        1      active sync   /dev/sda1
```

and, rather dissapointingly ...

```
mdadm: cannot open /dev/md1: No such file or directory
```

You are right, as I was having problems with the NAS I did try replacing the poorer disk with a new disk hoping that would cause it to spring back into life ... it didn't. And it confirmed to me that there was a fault with the device itself, not just a disk problem. It sounds like trying that did not help. Sorry for that.

When I look at the disk utility it tells me that each disk has two RAID components. One of 1GB (sda1 and sdb1) and one of 999GB (sda2 and sdb2). I am assuming that the data is in the "2"s and the "1"s are maybe where the device keeps some software etc.

In case it helps, here are the latest "sudo mdadm --examine /dev/sdX2" results:

```
/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sat May 19 05:43:43 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 1

    Update Time : Sun May 20 15:08:26 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 82b4eeca - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      spare   /dev/sda2

   0     0       8        2        0      spare   /dev/sda2
   1     1       8       18        1      spare   /dev/sdb2
```

and

```
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sat May 19 05:43:43 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 1

    Update Time : Sun May 20 15:08:26 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 82b4eedc - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      spare   /dev/sdb2

   0     0       8        2        0      spare   /dev/sda2
   1     1       8       18        1      spare   /dev/sdb2
```

I have a feeling I need to go down the "pull everything apart route" that you talked about. Sounds fun! :-)

---

### Post by steeldriver on 2012-05-21
I was wondering if you'd tossed the whole thing out the window in frustration

Right. So my concern given the history of the failure is that if you DO get it to assemble, it MAY resync whatever tut was on the spare drive over the top of your good data. I don't know enough about RAID to know whether that is likely or even possible.

What you do next should depend on how important this data is to you. You may want to consider make a low-level copy of the entire partitions (e.g. dd or partimage) before you do anything further.

I guess we already have copies of the RAID metadata on this forum, but I suggest also doing

```
$ sudo mdadm --examine /dev/sd[ab]2 > raid.status
```and saving the file somewhere permanent e.g. another USB stick since you are doing this all from Live boot.

Having thought about this some more this morning, I think **since this was a RAID1 (mirror) array there is nothing to be gained by trying to force assemble / create / add the other ('Spare') device**. What I would do next is simply try to mount md0 (the one that appears to have assembled - and started - with the single supposed good device). I would try:

```
$ sudo fdisk -l
```to see if it is now showing an fs type for md0 (mine doesn't - but I think that's because I'm running LVM2 on top so there's no actual fs directly on my md), otherwise I would guess and try ext3

```

$ sudo mkdir /mnt/raida

$ sudo mount -t ext3 -o ro /dev/md0 /mnt/raida

```

---

### Post by kindastuck on 2012-05-21
Hi Steeldriver,

Maybe I should have thrown it out the window!!! :-)

OK, I think you are right about taking a low level copy first. So i'll find a disk to do that with (I'm guessing it will take a little while ... to find the disk as well as to do the copy!) and report back. (I assume I need to copy this onto an empty drive in the PC, I couldn't copy it across the network into spare space on an extisting drive?)

---

### Post by steeldriver on 2012-05-21
well I've run partimage off a systemrescue cd to image a ~100GB laptop drive direct to an nfs-mounted NAS share so yes that should be possible to do that - for a TB drive you're right though, it will take a while ;)

fwiw I think simply attempting to mount the md0 device ro should be fairly safe - I was more recommending it before trying any of the more forceful mdadm assemble / create / add operations - your call though

---

### Post by kindastuck on 2012-05-22
Well the dd copy has been running for about 6 hours now .... 

A progress bar  .... or any hint of life .... would be really useful. 

I wish I'd tried the mount first.

ho hum :-)

---

### Post by RED666 on 2012-11-28
So.. WAS THIS ISSUE SOLVED?? I was so happy to find this post... sadly no clear solution.

My problem is similar. Unable to access 2disk mirror in my NAS, I'm sure the disks haven't failed physically.
Now I'm trying to access them with an USB Live version of Ubuntu.. In the Disks utility I can see the drive but other than "Software RAID Component (version 0.90.0) ",no further information is given and it can't be mounted.

I'm still under warranty, but the support people are no help at all and ALL MY DATA's on there ! To make it worse I found this article on my nas:
[http://www.randomtech.be/2012/03/26/sitecom-md-254-review-tutorial-guide-information/](http://www.randomtech.be/2012/03/26/sitecom-md-254-review-tutorial-guide-information/)

Please put me out of my misery. ;)

---

