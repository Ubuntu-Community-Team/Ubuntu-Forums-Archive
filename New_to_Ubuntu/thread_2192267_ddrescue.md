---
title: "ddrescue"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by darkxion on 2013-12-06
Ok..so firstly. I'm a noob messing with things I realize now I  shouldn't have been. I was trying to follow a guide using ddrescue to  recover data off a hard drive that crashed/has bad sectors. Both my  internal and external hard drive are/were NTFS windows partitions.
  I used Command: sudo ddrescue /dev/sda2 /dev/sdc /home/ddrescue.log where sda2 was the bad partition on my internal hard drive and sdc was my external hard drive. 
  I thought it would copy to a folder, well, I just hosed my partitions  on my external hard drive, now it won't mount. Is it screwed, is it  fixable? Please save me from my noobness, there is a great deal of important data on this 2tb external hd.

---

### Post by hansdown on 2013-12-07
Welcome to the forum, darkxion.

Using a live install disc, usb, etc., open a terminal with

```
cntrl>alt + f1
```

Type

```
gksudo nautilus
```

If you can see the drive in question, click on it, and transfer your files to a thumbdrive, etc.

---

### Post by darkxion on 2013-12-07
Yeah, doesn't show up. :( The partition info looks messed up bad

Disk /dev/sdc: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
/dev/sdc2   ?  1917848077  2462285169   272218546+  73  Unknown
/dev/sdc3   ?  1818575915  2362751050   272087568   2b  Unknown
/dev/sdc4   ?  2844524554  2844579527       27487   61  SpeedStor

Partition table entries are not in disk order.

---

### Post by hansdown on 2013-12-07
Are you able to post a link to the guide you were following?

Also, which version of linux you are using?

Thanks.

---

### Post by darkxion on 2013-12-07
I'm using 12.04 LTS, from a usb drive.

This is what I was using [http://ubuntu-rescue-remix.org/node/150](http://ubuntu-rescue-remix.org/node/150)] but that doesn't matter now. I wish I'd just wiped my internal hard drive and moved on. The only command I used (that caused this) was: "sudo ddrescue /dev/sda2 /dev/sdc /home/ddrescue.log" where /dev/sda2 was the partition on my bad 750GB internal drive and "/dev/sdc" is my 2TB external hard drive. It had one perfectly healthy partition, which was about 1.8TB, and there was about 750GB of free space left. Of the 4 new partitions on my drive, the first 3 (sdc1, sdc2 and sdc3) only seem to about equal the amount of free space I had on my drive. Coincidence? I think what I was supposed to do was this, "sudo dd if=/dev/sda2 of=dev/sdc/backup.img" not that it matters now..

I remember that I looked on my drive for what was recovered, and found nothing new, not really understanding what had happened. I then listened to some music on my external drive, and watched a video. Everything seemed normal, but when I rebooted later, it wouldn't mount anymore and I found all those partitions and my original partition was gone.  I suspect most if all my data is still there, I just need to know how to fix it. The stuff on my external drive is irreplaceable and important. :( Careless and stupid of me to ever even use it for this at all, especially not knowing exactly what I was doing. 

ALSO: I will do whatever I need to do to fix my external drive and recover my data. Today I am going bestbuy to get a new internal hard drive, and I am reinstalling windows. I am also going to buy a 3tb hard drive so I can make an image of my 2tb hard drive before any recovery starts. Anything I have to do, just tell me. I can't lose this data, if I have a choice.

So what someone told me was that I need to make a copy of this drive on another drive, before I try any recovery, in case I screw it up even worse than I already have, then use testdisk on it. They didn't really give me any instructions on how, though. I've already accepted that at the least I've lost some of this data, easily the 700GB or so from these new partitions, perhaps ALL of the data. Any help would be considered divine intervention at this point. I am hoping that even though DD overwrote a good chunk of my drive, given the size of my drive at least SOME data is still intact..

WELL, I tried to use clonezilla to copy my external drive as an image to my new 3TB drive, but clonezilla doesn't much like how screwed up the partitions are, and won't do it. :\
I don't feel comfortable enough with DD after what I've already done to do it with DD.

---

### Post by rubylaser on 2013-12-07
I'm sorry to hear this happened to you.  There is a reason that dd has the nickname Data Destroyer :-( It is a great tool, but it can go sideways in a hurry with one wrong command.  Since you ddrescued to the whole drive, it's unlikely you will ever be able to recover the partitions.  One option would be to use a program like Photorec to try to recover the individual files.  Unfortunately, this will just recover files and will not retain folder structure or even filenames.  But, if your data is irreplaceable, this is what I would do in lieu of having a backup.

---

### Post by darkxion on 2013-12-07
At the end of the day I don't care about the partitions at all, I just need my files. Not being able to retain filenames would be pretty terrible but not as bad as losing the files at all, not by a long shot. At least some of that data must still be there and accessible, otherwise how could I have been watching videos and listening to music on thayt drive AFTER I ddrescue'd (but before I rebooted and now couldn't mount) ? I'm not ready to accept defeat yet. Hopefully someone here may have some tips. :( 

Update: I'm currently backing up the entire drive 2TB drive to a disk img on my empty 3TB drive. If anyone has any tips on how to test repairing this image, or extracting data, I would really appreciate it.

---

### Post by philinux on 2013-12-07
Read up on testdisk and one of its included apps photorec. Photorec csn recover all sorts of files.

---

### Post by darkxion on 2013-12-07
Will do..thanks

---

