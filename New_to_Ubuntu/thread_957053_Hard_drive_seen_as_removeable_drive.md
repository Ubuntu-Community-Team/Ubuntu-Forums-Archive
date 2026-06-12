---
title: "Hard drive seen as removeable drive"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by wawadave on 2008-10-23
1. I added a 250 gig hard drive that had been formatted and partitioned under xp.its installed as a slave.
ubuntu sees its drives as removable media.how do i fix that?

2. It allso calls all he new drives "new volume" ntfs partitions are in capitals. any easy fix for that?

 I originality added the drive to burn backup of data on it as xp would not boot with my new sony dvd writer installed.
ubuntu sees it boots with it burns with it no problem. lol 
nice to see linux use hardware and windows cannot!!!

3. But ubuntu only see,s 4.2 gigs on dvd,s. but then so did xp same media dvd,s say 4.7  mother board is an older soyo 1200ghz amd cpu 256 megs of ram. if that would make a difference. 
looked in search on these before found some ideas. 
But though i have been useing ubuntu for a while now i,m still not to far above a newby.

I,m allso dyslexic and trying to manually type some command line task in terminal is very difficult for me.

---

### Post by quirks on 2008-10-24
> 1. I added a 250 gig hard drive that had been formatted and partitioned under xp.its installed as a slave.
ubuntu sees its drives as removable media.how do i fix that?

I believe, you must add the volume to your /etc/fstab and mount it somewhere other than /media. Then it won't be shown as a removable drive anymore. Do you know how to do that?

As for the other two questions, I do not know for sure, how to fix them.

---

### Post by Liviu-Theodor on 2008-10-24
Run the following in terminal:
```
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
The first command gives the UUID for each partition. At the last command, insert the partition, with the mount points that you wish (ie [FONT="Courier New"]/home[/FONT]), but be sure to declare it as ntfs formatted.

You can copy-paste commands in the terminal.

And for the third question, it is possible that the dvd's only have that much on them, nothing to worry about.

---

### Post by quirks on 2008-10-24
I think, I found a way how to label your NTFS partition (I knew how to do it for ext3, but not for NTFS). You can find the instructions in the Help Wiki:

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by wawadave on 2008-10-24
I,ll give these a try thank you!!

And the dvd,s are 4.7 gigs capacity. only seeing 4.2gigs when burning or reading.

---

