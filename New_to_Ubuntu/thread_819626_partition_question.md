---
title: "partition question"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by d4ng3r on 2008-06-05
I am planning to reformat my computer (dual boot with Ubuntu 8.10 and Win XP) and just had a quick question on Mount Points.  I would like to split my hard drive 40-40-40 giving Ubuntu and Windows both 40 gb and then a FAT32 as shared space, for Music and pictures and such so I don't have to fuss with NTFS on Linux or vice versa.  Now my question is when running the Ubuntu partitioner, What mount point would I assign the FAT32 partition, or do I not need to assign it any.  I know last time I tried to put my /home on a different partition for some reason it failed and I had this drive it named 3.3gb volume that I needed to enter to root pw to look at, and everything in it was locked, and id like that to not happen again.

Thank you for any help.
-Brian

---

### Post by neurostu on 2008-06-05
You don't want to assing a mount point to the fat32 partition.
Make 4 partitions:
1 - windows install
2 - Shared Fat32 space
3 - Linux install  - mount point /
4 - Linux swap

---

### Post by neurostu on 2008-06-05
Ubuntu should automatically detect the fat32 partition and mount it to /media/ when you install (plus it will place a link to it on your desktop too)

---

### Post by melrom on 2008-06-05
linux is good at handling ntfs nowadays. you sure you wanna go with fat32?

---

### Post by notwen on 2008-06-05
Any additional drives generally populate your systems /media folder.  I normally just mount all my additional storage hdds under it.  

For example:

sda1 would get amount point of /media/sda1
sdb1 would get amount point of /media/sdb1
and so on.  

Since your partition will mainly be used as a shared drive /media/shared is also an easy option.  Post back if you have any questions.  Hope this helps.  =]

---

### Post by neurostu on 2008-06-05
You shouldn't have to specify /media/sda1 in the partition editor during the install, ubuntu will do it automatically for you on boot.

---

### Post by 7aboobs on 2008-07-15
i did exactly the same, but my fat32 seems to be mounter to media/sda0 and there's a locked side beside it in gparted. and i can't create folder or edit the fat32 partition. how do i enable this?

last time i just reformatted the partition, then only could i edit anything in it altho copying files from the ext3 partition to the fat32 was very very slow, nvr reachin beyong 1.8 mbs.

---

