---
title: "[SOLVED] Easy question...help me out"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by timstone on 2008-10-04
When I installed Ubuntu I had already had WinXP installed.  I had 3 partitions divided between 2 hard drives, When just looking through the menu I saw I have a removeable drive that is like 27.5 gig, and also when looking through and checking the disk usage it says there is a total of  168.7 GB of system space...with 9.8GB being used 

My question is what command can I throw into a terminal window to find out where the other partitions are, or if they are still windows partitons (NTFS) how do i pull them up?

---

### Post by Elfy on 2008-10-04
```
sudo fdisk -l
``` will list all your partitions.

```
df -h
``` will tell you what partitions are mounted

---

