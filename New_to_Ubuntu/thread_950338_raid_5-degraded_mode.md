---
title: "raid 5-degraded mode"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by sazan on 2008-10-17
i wanted to post this thread in 'server platforms' but didnt hav privilege to post it there and i really need to understand this so m posting this thread here.. 

1. Raid -5 needs at least 3 disks for it to a clean raid.... but mdadm in linux allows raid-5 with 2 disks.. how is that possible which contadicts raid-5 definition??

i saw a similar thread discussion but i cudn't get any valuable output from it.. 

2. what exactly goes on with other 2 disks when 1 disk fails (i.e. degraded mode) .. ?? (i mean wat is happening until the third or spare disk is added)/(what happens in degraded mode???)

people plz giv me ur inputs ??

---

### Post by nhasian on 2008-10-17
you are correct.  for RAID5 you need at least 3 disks.  

from wikipedia:

RAID 5 (striped disks with parity) combines three or more disks in a way that protects data against loss of any one disk; the storage capacity of the array is reduced by one disk.

if you only have two discs you can do mirroring for redundancy or striping for speed.

the fastest is if you use 4 drives for RAID 10:

RAID 10 (or 1+0) uses both striping and mirroring.

---

### Post by sazan on 2008-10-17
> **nhasian said:**
> you are correct.  for RAID5 you need at least 3 disks.  

from wikipedia:

RAID 5 (striped disks with parity) combines three or more disks in a way that protects data against loss of any one disk; the storage capacity of the array is reduced by one disk.

if you only have two discs you can do mirroring for redundancy or striping for speed.

the fastest is if you use 4 drives for RAID 10:

RAID 10 (or 1+0) uses both striping and mirroring.


my question still lies there when raid-5 needs min of 3 disks then how does '**mdadm**'allow it.. i mean there must be some logical reasoning for it .. isn't it ??

---

