---
title: "Lost  100gigs drivespace somewhere"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-05-08
I am not sure what happened I had Vista ultimate but I installed the newest ubuntu on the hard drive ( not duel boot) and well I checked to see how much hd space I have and out of 320gigs it says in my (properties) file system says its using 12.2GB  and 180 GB free space and my media is 92.1 GB I am wondering what happened to the rest of the HD because I was going to partition that part of the drive so I could put LSF (Linux From Scratch - Version 6.3) is there anyway for me to see where or find out what happened to the space also how do I make a new partition ?

---

### Post by NightwishFan on 2008-05-08
paste this into terminal "its a lowercase L"
```
sudo fdisk -l
```

---

### Post by Shadowmeph on 2008-05-08
> **NightwishFan said:**
> paste this into terminal "its a lowercase L"
```
sudo fdisk -l
```

thanks that gave me this ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11197    89939871   83  Linux
/dev/sda2           38898       38913      128520   83  Linux
/dev/sda3           11198       38897   222500250    5  Extended
/dev/sda5           11198       38145   216459778+  83  Linux
/dev/sda6           38146       38897     6040408+  82  Linux swap / Solaris
``` which I am wondering why it looks like I have six partitions when I should only have maybe 3 lol how can I change this without reinstalling everything and what is the extended?

---

### Post by kwacka on 2008-05-08
maximum number of partitions you could have on a hard drive was 4 (don't know if this has changed). A way to get around this was to use 'extended patrition, to act as a container for extra partitions.

Your extended partition contains the two partitions sda5 & 6 (compare block starts of sda3 & 5, & final blocks of sda3 & sda6).

Can you check the contents of sda2 & sda5?

---

### Post by NightwishFan on 2008-05-08
It appears you have 2 Linux partitions (doesnt means its an os) along with Ubuntu. (Which is the extended) Are they seperate home? I wouldnt think so but that might be the case.

---

### Post by dark_harmonics on 2008-05-08
your drive looks to be in a partitioning nightmare. if this was my system i would copy my stuff off it and re-partition it right from the start. I hate partitioning tools as i find that they sometimes can do more harm then good. 

Anyhow before you "fix" anything you should definitely backup your data. Who here hasn't thought "oh it will be an easy fix" only to find out you killed your home partition. DOH!

---

### Post by Shadowmeph on 2008-05-08
> **dark_harmonics said:**
> your drive looks to be in a partitioning nightmare. if this was my system i would copy my stuff off it and re-partition it right from the start. I hate partitioning tools as i find that they sometimes can do more harm then good. 

Anyhow before you "fix" anything you should definitely backup your data. Who here hasn't thought "oh it will be an easy fix" only to find out you killed your home partition. DOH!

well fortunately I just installed yesterday so I later on I am going to start from scratch I totally messed it up last time because I got confused so 
what are the recommended partitions like for swap file and such I do want to install LFS (Linux from scratch) on a small partition

---

### Post by NightwishFan on 2008-05-08
Pre-prepare a partition for the other OS, if only to just reserve the space, then use the "Use largest continuous free space option" It will give something like:

partition1: empty reserved ext3 partition (which you can delete later for Linux for scratch)
partition2: extended
partition5: ext3 (ubuntu)
partition6: swap

---

### Post by Shadowmeph on 2008-05-08
> **NightwishFan said:**
> Pre-prepare a partition for the other OS, if only to just reserve the space, then use the "Use largest continuous free space option" It will give something like:

partition1: empty reserved ext3 partition (which you can delete later for Linux for scratch)
partition2: extended
partition5: ext3 (ubuntu)
partition6: swap

aww that makes sense thank you

---

