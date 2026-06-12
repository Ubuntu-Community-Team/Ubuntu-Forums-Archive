---
title: "Ubuntu Server set up help"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by sbaig on 2014-08-05
Hello all,
So I am basically trying to use my old desktop as a file share server for my home office. I would like as much space as possible on both hard disks to store my files, so I am not sure how I should be partitioning this. I know theres a few configurations in the install as well as a manual option but I am a complete novice at this and would appreciate if someone could point me in the right direction. I have no idea what e3 vs e4 mean, and I have read a great many different guides and am still lost. I had windows installed on this computer and I think the first botched install by me has deleted it (which is what I wanted).

Primary HDD: 250 GB
2nd HDD: 3 TB

I think I messed up something with the installation because after the install completed, I removed the USB and after the initial bios load etc.. ubuntu will simply not load and im left with a black screen so I will try and reinstall.


Thanks!

---

### Post by cj13579 on 2014-08-05
I have something similar in my home but share media rather than documents/office stuff. I haven't installed Ubuntu for a while so I am not sure about the e3ve4 though that will probably relate to EXT3 and EXT4 which are filesystem types like NTFS and FAT. [This]("http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/") is a pretty good article on the differences between those two. Try and install using the Live CD (once you have made a full backup of everything you want from both disks) and let Ubuntu have the whole disk.

Also, it may be a related to media rather than office and document but [this guide]("http://www.havetheknowhow.com/") is very detailed and excellent for building a home Linux server.

---

### Post by mastablasta on 2014-08-06
since you are new at this whole thing why not sue a distribution where some things are preinstalled for you. have a look at Zentyal - it's Ubutnu based and they have a free community edition. They also have a nice point and lcick web interface and the whole thing was made with small offices or home server in mind.

as for partitioning you can create partitions later. if you use default ubuntu the install will create the necessary partitions for you. you an later make a data partition for data only. the second disk will porbabyl have to be set to be automounted. you an have more partition on that one as well.

on older BIOS hardware you need just root (/) and /swap. root is like C: in windows, swap is like pagefile in windows and should be twice size of ram or 4 GB max is enough. in other words if you have 2 GB or less ram make it double size. if you have 2-4 GB or more just make it the size of ram. this is only needed if you partition manually. then you can create data partitions. just make sure you leave some room for root partition. if you give it 20-30 GB it should be more than enough for server, probably even 10 Gb would be more than enough..


if you use server only for saving and retrieving data you can also look at 2 other good options with a GUI interface:
Openmediavalut - based on Linux Debian stable I believe
FreeNAS - Based on FreeBSD - descendant of Unix, this is not Linux. but it is similar in many ways.

---

### Post by TheFu on 2014-08-06
Not directly related, but [Linux Explained for Windows]("http://blog.jdpfu.com/Lin_4_Win_Users") Users.

---

