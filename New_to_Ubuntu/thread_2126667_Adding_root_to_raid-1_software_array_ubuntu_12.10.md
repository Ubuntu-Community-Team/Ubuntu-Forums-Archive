---
title: "Adding /root to raid-1 software array ubuntu 12.10"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by EddieCurrents on 2013-03-17
Hello,

newbie here.  I'm building a file/samba/print server at home.  I've to two 1TB drives in it and I'd like to make a RAID-1 array and do additional backups with LVM snapshots.

So here's my partitioning scheme so far (fdisk -l)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d39b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      585727      291840   83  Linux
/dev/sda2          585728    16586751     8000512   82  Linux swap / Solaris
/dev/sda3        16588798  1953523711   968467457    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5        16588800  1953523711   968467456   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008601d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      585727      291840   83  Linux
/dev/sdb2          585728    16586751     8000512   82  Linux swap / Solaris
/dev/sdb3        16588798  1953523711   968467457    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sdb5        16588800  1953523711   968467456   83  Linux

Mount points are /dev/sda1 (/boot) and /dev/sda5 (/) sda2 and sdb2 are swap files (which I take to understand are striped by the kernal?)

So, what I'd like to do is have sda5 and sdb5 in raid-1 and use lvm snapshots to do additional backups and whatnot.

I've searched google and these forums but I suspect I suck at searching for the solution because I didn't find it so far.  I've looked at the mdadm wiki but if the answer is there I can't find it.

I'd really appreciate a really dumbed down explaination of how to accomplish this.  Thanks in advance.

---

### Post by EddieCurrents on 2013-03-18
Solved.... sort of

It was a new build with nothing on it, so I started over with Ubuntu 12.10 server which allowed me to install lvm over software raid in the installer and then I installed ubuntu-desktop.

---

