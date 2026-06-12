---
title: "Hard disk won't mount"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by Noor1101 on 2013-01-17
Hi,

I have a 2.5" 500GB harddisk in a casing that won't mount (or at least cannot be accessed and is not shown in "Disk Usage Analyzer") (and it can't be accessed in Win XP either).

I twiddled too much with it when I was trying to make it work as an internal hdd for my laptop. _I think I formatted some kind of crucial bit of the disk._ (As you've probably noticed I don't really know much about these things.)

(In the end it turned out the disk didn't work properly _inside_ my laptop because my BIOS is outdated and can't handle 500GB.)

It HAS worked properly before in its casing.

I ran sudo fdisk -l:

[B](see post #5)
[/B]^ and it seems the disk is detected (sdc)

it's a Western Digital Scorpio Blue 500GB - SATA-300 - 8MB buffer - 5400 rpm


I'd like to sell this disk (or swap it against a smaller one) because I'm too scared to ruin my laptop trying to update the BIOS -- but I of course have to get the disk to work again first.


Thanks for any help you can offer :)

Regards

Noor

---

### Post by NikTh on 2013-01-17
Hi , 
I did not understand what exactly you want to achieve. If your BIOS is outdated and cannot handle a HDD of 500GB , then is a fault of BIOS . OK, we "solved" that. 

What about the disk now ? Do you want to wipe it  ? The disk seems to be detected properly with all its partitions .. etc.. 

If you want to see if is healthy or not.. then run smartmontools.. 

```
sudo apt-get install smartmontools --no-install-recommends 
sudo smartctl -a /dev/sdc
```The second command maybe wants to run it twice (because of the external case) to show full results. 

Post back here the results .. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by Noor1101 on 2013-01-17
OK, sorry, a little more info then :)

1- I bought a 2.5" (Seagate) internal hdd for my laptop
2- It didn't work (because of my outdated BIOS, but I didn't know that then)
3- I returned it to the store and got a Western Digital hdd with the same specs back for it
4- It still didn't work (again because of the BIOS, still didn't know)
5- I bought a casing with USB connection to use it as an external disk
6- It worked perfectly
7- I tried many things, hoping to get it to work as an internal disk
8- I think I formatted some kind of (small) partition that I shouldn't have formatted. I don't know, but maybe some kind of controller / factory settings / operating 'manual' for my laptop to recognise the disk and to understand how to mount / use it?
9- Since then the USB-connected hdd can not be opened or browsed in my Ubuntu, nor on my friend's Win XP (although it was listed in the outcome of Ubuntu's 'fdisk -l')

10- Now I want to fix this, so that I can sell the disk or swap it for a smaller internal disk, to use in my laptop.

Is there such a small partition on a disk that one shouldn't format? 
And if there is, is there a way to fix it?
Or must it be something else that went wrong?

I'll get back in (half) an hour or so to post the results of smartmontools. Dinner's ready.

Thanks

---

### Post by bab1 on 2013-01-17
> **Noor1101 said:**
> OK, sorry, a little more info then :)

1- I bought a 2.5" (Seagate) internal hdd for my laptop
2- It didn't work (because of my outdated BIOS, but I didn't know that then)
3- I returned it to the store and got a Western Digital hdd with the same specs back for it
4- It still didn't work (again because of the BIOS, still didn't know)
5- I bought a casing with USB connection to use it as an external disk
6- It worked perfectly
7- I tried many things, hoping to get it to work as an internal disk
8- I think I formatted some kind of (small) partition that I shouldn't have formatted. I don't know, but maybe some kind of controller / factory settings / operating 'manual' for my laptop to recognise the disk and to understand how to mount / use it?
9- Since then the USB-connected hdd can not be opened or browsed in my Ubuntu, nor on my friend's Win XP (although it was listed in the outcome of Ubuntu's 'fdisk -l')

10- Now I want to fix this, so that I can sell the disk or swap it for a smaller internal disk, to use in my laptop.

Is there such a small partition on a disk that one shouldn't format? 
And if there is, is there a way to fix it?
Or must it be something else that went wrong?

I'll get back in (half) an hour or so to post the results of smartmontools. Dinner's ready.

Thanks
I don't see a problem with the BIOS seeing the drive or that the drive is "too big".  The problem is that it is a SATA drive and the laptop has no provision for SATA interfaces.  It sounds like this is an *_interface issue _* not a BIOS issue.  

If this were a BIOS issue the drive would not have worked in the external USB casing. When you installed the drive in the external USB case the SATA was converted to a USB interface. Both of these are serial interfaces that's why a SATA drive will work on a USB interface.

If the disk test is successful (and I'm sure it will be) you need to format the disk.  At that point it will work for you as long as you use the USB interface.  If you want to install a disk that will work internally,then you will most probably need a PATA internal drive rather than a SATA drive.  Check the laptop specifications and see which type of drive interface is needed (PATA or SATA).

---

### Post by Noor1101 on 2013-01-17
```
noor@laptop:~$ sudo smartctl -a /dev/sdc
[sudo] password for noor: 
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-35-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
noor@laptop:~$ 

```I'm sorry for the confusion, but the sudo fdisk -l output I copied into my first post was wrong, it was an old one from when the disk still worked. This is the correct one:
```
noor@laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00034841

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   111185919    55591936   83  Linux
/dev/sda2       111187966   117209087     3010561    5  Extended
/dev/sda5       111187968   117209087     3010560   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ffd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux
noor@laptop:~$ 

```I cannot access the disk, and in 'Disk Utility' - Peripheral Devices - 500 GB Hard Disk, it says under "Volumes":
Unknown
500 GB

I have tried formatting the drive (Master Boot Record) and volume (tried both Ext4 and FAT) but that doesn't solve anything:
The volume can still not be mounted, and after restarting "Disk Utility" it says "Unknown" again (instead of Ext4 or FAT)

I think this is the most important question: Is there a small partition on a disk that one shouldn't format? 
(But I might be wrong there)

bab1, do you mean to say that if my BIOS cannot handle a 500GB internal disk, it can also not handle a 500GB external disk? That's new info for me. I have a 1.5TB external disk that works fine.
(By the way, it can't be Just my BIOS, because the disk doesn't work in my friend's laptop's Win XP either)

Thanks for your help

---

### Post by d4m1r on 2013-01-17
Honestly, if the disk is not physically/electrically damaged from static or the like when you were in/uninstalling it, it would just be easier to update your BIOS so you could use it....

This would save you having to sell it and purchase another, and updating BIOS' has been been straightforward and relatively risk free for at least a decade now. What kind of laptop is it? Made/model/specs.

---

### Post by Noor1101 on 2013-01-17
Thank you d4m1r, I might have to do that some time.

But the thing is, I know I ruined _something_ on the disk. It used to work in its casing, and now it doesn't. So if I upgrade my BIOS now and put the disk inside the laptop, I doubt it will work. Because it doesn't now, and it used to, before I formatted / deleted (too many of the) partitions.

I'll put in some screenshots. The SATA/PATA stuff is over my head, but I know that the 60GB internal hdd that is in my laptop now is SATA and it works well.

The fact that two (Seagate and Western Digital) new 500 GB hdd's were error-free but both didn't work inside my laptop, got me to believe that it was a (BIOS /) capacity issue, and not physical/electrical damage. It might be that after the formatting the 2nd hdd was damaged, but I doubt it. I'm always very careful with it.

---

### Post by bab1 on 2013-01-17
> **Noor1101 said:**
> Thank you d4m1r, I might have to do that some time.

But the thing is, I know I ruined _something_ on the disk. It used to work in its casing, and now it doesn't. So if I upgrade my BIOS now and put the disk inside the laptop, I doubt it will work. Because it doesn't now, and it used to, before I formatted / deleted (too many of the) partitions.

I'll put in some screenshots. The SATA/PATA stuff is over my head, but I know that the 60GB internal hdd that is in my laptop now is SATA and it works well.

The fact that two (Seagate and Western Digital) new 500 GB hdd's were error-free but both didn't work inside my laptop, got me to believe that it was a (BIOS /) capacity issue, and not physical/electrical damage. It might be that after the formatting the 2nd hdd was damaged, but I doubt it. I'm always very careful with it.

We're all over the map here.  If you can see the drive then the BIOS is fine.  There are 2 setings in BIOS on for SATA and one for PATA compatible.  Neither setting has anything to do with your capacity limits on your 500GB drive.

If you have corrupted the data on the drive then it wont mount.  I belive that is the case here.  No capacity issues, not small partition.  Just plain old corrupted data.

Did you disconnect the drive without unmounting it maybe?

I assume the data is lost.  Is this going to the only drive in the laptop?

[COLOR="Blue"]Edit: I have looked at the snapshots.  The dirve looks to be fine.  There appears to be a second port to install this drive in the laptop.  If are planning to install it as a second drive, I would format it first in the external enclosure, If that works you can transfer it to the laptop.  [/COLOR]

---

### Post by Noor1101 on 2013-01-17
There luckily was never any data on the disk as I couldn't get it to work in my laptop, and I already had an external disk :)

I have formatted and reformatted but it just won't mount, and the filesystem keeps being called 'Unknown' after having safely removed the disk and connected it again.

I just want to get this disk to work[COLOR=Blue] - not inside the laptop, but in its casing -[/COLOR] : make it into one FAT32 partition and have it stay that way, being mountable and unmountable..

I don't know if this means much to you, but anyway:
```

noor@laptop:~$ sudo fsck /dev/sdc1
[sudo] password for noor: 
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

noor@laptop:~$ sudo e2fsck -b 8193 /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

noor@laptop:~$ 

```Maybe it's just broken beyond repair?


Thanks to all

---

### Post by Noor1101 on 2013-01-17
> **bab1 said:**
> 

[COLOR=Blue]Edit: I have looked at the snapshots.  The dirve looks to be fine.   [/COLOR]

I think (?) you were looking at my -properly working- 60GB internal hdd. I put in that screenshot to show it's SATA, and it works. Sorry, I should have been clearer about that.
 The third and fourth screenshots show the 2 ways in which Disk Utility displays the faulty 500GB disk.

Thanks :)

---

### Post by sandyd on 2013-01-17
> **Noor1101 said:**
> There luckily was never any data on the disk as I couldn't get it to work in my laptop, and I already had an external disk :)

I have formatted and reformatted but it just won't mount, and the filesystem keeps being called 'Unknown' after having safely removed the disk and connected it again.

I just want to get this disk to work[COLOR=Blue] - not inside the laptop, but in its casing -[/COLOR] : make it into one FAT32 partition and have it stay that way, being mountable and unmountable..

I don't know if this means much to you, but anyway:
```

noor@laptop:~$ sudo fsck /dev/sdc1
[sudo] password for noor: 
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

noor@laptop:~$ sudo e2fsck -b 8193 /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

noor@laptop:~$ 

```Maybe it's just broken beyond repair?


Thanks to all
Have you tried recreating a new partition table with gparted?

---

### Post by Noor1101 on 2013-01-17
Hi Sandyd,

Thanks for your reply. 
I hadn't tried that, but now I have. In Gparted I created a new partition table (MS-DOS (=default)), and made a new partition (Primary partition, FAT32, the entire disk (465 GB))

It said "Operation successful" (or something alike) but then, once more, "Unallocated" with a red exclamation mark. Partition -> Information brings up a window that says

> File system: unallocated
Size: 465.76 GiB

First sector: 0
Last sector: 976773165
Total sectors: 976773166

[COLOR=Red](Exclamation mark)[/COLOR] Warning:
/dev/sdc: unrecognised disk labelAfter that the partition table was gone.
I tried this a couple of times, but the error comes up every time. Unrecognised disk label.


:(


[SIZE=1]...[SIZE=1]the disk is ruined, isn't i[SIZE=1]t[/SIZE][/SIZE]...



[/SIZE]edit: Having read [this thread]("http://ubuntuforums.org/showthread.php?t=1922371&page=3") I think I'll try to borrow a different casing (external enclosure) from someone and see if it works then..

---

### Post by bab1 on 2013-01-17
> **Noor1101 said:**
> Hi Sandyd,

Thanks for your reply. 
I hadn't tried that, but now I have. In Gparted I created a new partition table (MS-DOS (=default)), and made a new partition (Primary partition, FAT32, the entire disk (465 GB))

It said "Operation successful" (or something alike) but then, once more, "Unallocated" with a red exclamation mark. Partition -> Information brings up a window that says

After that the partition table was gone.
I tried this a couple of times, but the error comes up every time. Unrecognised disk label.


:(


[SIZE=1]...[SIZE=1]the disk is ruined, isn't i[SIZE=1]t[/SIZE][/SIZE]...





[/SIZE]edit: Having read [this thread]("http://ubuntuforums.org/showthread.php?t=1922371&page=3") I think I'll try to borrow a different casing (external enclosure) from someone and see if it works then..
Pretty negative thoughts there.  I would remove all partitions on that drive and create a new single partition (no ms-dos  needed).  Then format the partition as EXT4.  Then see if mount the new partition to the file system.  There are structural problems with large partitions at FAT32.  If you want to try a windows partition then try NTFS.  If your feel you must create a FAT32 partition create a partition less than 32GB (maybe under 8GB).

---

### Post by Noor1101 on 2013-01-18
Thank you all very much for your help. I will go and see a friend who is good with stuff like this (although he does use Windows :P).. and who will probably be able to connect it directly to his pc via a SATA port. I'll let you know how that goes.

If anyone has any more thoughts, they would be greatly appreciated.

---

