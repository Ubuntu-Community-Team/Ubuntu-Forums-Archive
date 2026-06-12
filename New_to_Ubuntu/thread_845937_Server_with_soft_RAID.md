---
title: "Server with soft RAID"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by wax4213 on 2008-07-01
I have a Shuttle with two identical 750 GB HDDs that I would like to setup as a personal media server for my XP laptop and PS3, eventually accessible over the internet.  My primary question at the moment is how best to setup my soft RAID.

My ideas for a reasonably stable RAID, barring HDD failure, are as follows.  Keep in mind that I've never set up a RAID before.

Partition the two drives identically, however, the uses of the partitions on each drive will be different.  On one drive will be a boot partition and swap partition with the rest dedicated to a RAID 0.  The second drive will have / and possibly /home or /var, with the rest of the partition also dedicated to the RAID.

Any thoughts or suggestions?  Everything other than swap would probably be ext3.

---

### Post by cariboo on 2008-07-01
The first thing you should do is read this so you have an unsterstanding of what raid is:

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

To set up raid look here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Jim

---

### Post by wax4213 on 2008-07-01
Thanks for the links, I have actually read both of those pages.  From my understanding, I should be able to setup a software RAID with partitions instead of entire physical drives.  And the second link is for fake RAID, slightly different than what I'm looking for.

The reason I would like my boot, /, and swap partitions not part of the RAID is incase of some failure or another.  I should be able to still boot, assuming it's not one of the aformentioned partitions that got messed up.

Edit:  Please feel free to correct me if I have something completely wrong though.  I certainly don't claim to be an expert on matters such as this ^^

---

