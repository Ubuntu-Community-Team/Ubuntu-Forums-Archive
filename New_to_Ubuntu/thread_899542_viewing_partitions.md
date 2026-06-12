---
title: "viewing partitions"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by iceman1984 on 2008-08-24
Good day I recently installed ubuntu 8.04 and created 2 partitions. The first I set the mount point as root and the partition type as primary, the second I set the mount point as /home and partition as logical and the Filing as ext3. Everything installed fine however, when checking in computer I only see one File system. While searching through that file system I saw the /home file. What I'm puzzled at is where is the partitioned space and how do I get it to show in computer as an extra drive.

---

### Post by sandysandy on 2008-08-24
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

look for ur partitions under Places ----> Computer (top panel)

regards

---

### Post by sancho panza on 2008-08-24
From what I understand, the filesystem is mounted on / and all other system partitions are a part of the filesystem even though they are physically different drives. Linux does not display physical drives to the user, unlike windows. Showing physical drives makes no practical sense in general.

To confirm that you have the home on a seperate drive, check System>Admin>Sys monitor and view the filesystems tab to see all the drives on the computer.

Hope this helps,
Cheers!

---

### Post by aspergerian on 2008-08-24
> **sancho panza said:**
> Showing physical drives makes no practical sense in general.

I would like politely to disagree. I'm used to placing files onto a clearly delineated physical drive or partition thereon and find that approach quite useful. As a Linux noob, I guessed at partitioning while installing 8.04.1 into an Asus901 and, during that process, read many wikis and forum postings, which helped everything remain clear as mud. As I type this (via 901, 8.04.1), I'd like to find a clear presentation of each drive and each partition, and the usage on each. File browser doesn't seem to give me this. System monitor (file systems) almost does this but not quite. Part of the challenge of what's located on which partition - aside from noobiness - is that my 8.04.1 is on the 901.

---

