---
title: "Partitioning Question"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by psychofish25 on 2008-07-06
I am currently Dual-Booting Windows Vista and Ubuntu 7.10 Gutsy Gibbon. I have a 150GB standard hard drive that is partitioned into two parts for Windows Vista (OS and Recovery). I then purchased a 300GB HD and placed Ubuntu on it. It is partitioned into a 299,204.7 MB part and a 5,938.1 MB part, I guess for swapping resources. Now, I wish to install Mac OSX (with a crack run x86) on this computer. I wish to leave my Vista HD alone, and split up my Linux HD and give 20 GB to Mac OSX. I am now using Partition Magic and it will not allow me to break up the giant Linux Partition. Do I have to format that HD first before I can partition it? What else can I do so that I don't have to format it.

Thanks,
Jordan

---

### Post by apmcd47 on 2008-07-06
I think the only partitions safe to split are of the FAT variety. For all others you should resize them. Does your version of Partition Magic allow the resizing of Linux partitions? If so, use that. If not, I suggest you check to see if any of the live CDs you have in your possession contain gparted and use that. If you don't, download and burn the gparted live CD from [here]("http://gparted.sourceforge.net/livecd.php").

Before you start please back up essential data on your Linux partition (modified /etc, eg /etc/apt, and /home area) *Just in case*, either onto your Windows disk, or a CD, or even a tape drive! I have used Partition Magic years ago to resize NT partitions and had no problems, but best to be safe than sorry.

I hope this helps.

Andrew

---

### Post by annda on 2008-07-06
you can try the ubuntu live CD's gparted to resize the partition and then create one in the freed space.

---

### Post by kuja on 2008-07-06
The resize2fs command should be able to resize the filesystem for you, assuming it's not mounted. After that resizing the partition with your normal partition editor should be trivial I would think. Maybe you should think of trying something like the gparted live cd though ... it's pretty nice.

---

### Post by bilbo.san on 2008-07-06
Hey
Use Acronis Disk Director, install it on Windows, and from there, you can easily create partitions out of any disk free space on your pc (with exception of Swap Partitions). Increase, resize and delete partitions with no problem.
At least, that is what I used and worked just perfect... but do some research first.

Good luck.
b.

---

### Post by bumanie on 2008-07-06
The best thing to do is use vista's own partitioner to resize the vista partition - it really works best for vista. ubuntu will be able to partition the rest of the drive during installation.

---

### Post by psychofish25 on 2008-07-06
The problem is I want to parititon my LINUX HD, and I tried on Windows but it won't let me do so using its own partitioner. I've tried GParted as well but I seem to get the same results. If I delte a partition, is that the same as formatting it?

---

### Post by annda on 2008-07-06
> **psychofish25 said:**
>  I've tried GParted as well but I seem to get the same results. If I delte a partition, is that the same as formatting it?

deleting a partition is basically the same as telling the system that it doesn't exist anymore. so in that case you will need to crate another one in its place and format it.

BTW: what exactly is gparted saying? i can't imagine that the partition is full. can you post a screenshot if it's not too much trouble? also, you can only reclaim space after a partition you are shrinking, not before it - just in case this is what you are trying to do.

---

### Post by bumanie on 2008-07-06
> **bumanie said:**
> The best thing to do is use vista's own partitioner to resize the vista partition - it really works best for vista. ubuntu will be able to partition the rest of the drive during installation.

Sorry, I misread the original post. Gparted should work, but you have to have the partition you are working on unmounted, therefore do the partitioning off a live cd.

---

### Post by psychofish25 on 2008-07-06
Well I used my Live CD and tried GParted again. It then let me resize my old partition to make room for a new one. I must have been doing something wrong before.

Thanks for all the help.

---

