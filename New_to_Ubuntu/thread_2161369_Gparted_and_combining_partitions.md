---
title: "Gparted and combining partitions"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by yunone on 2013-07-10
I have a single SSD in my VAIO that i have formatted from the original Windows 8 install. When i enter Gparted there is two partitions, SDA and SDB and they both have a size of 119GB. I want a single partition, but am unable to merge the two unallocated spaces.
What can i do to make those two partitions into one logical space?

thank you in advance

---

### Post by Mark Phelps on 2013-07-10
You mention two partitions, but "sda" and "sdb" are DRIVE indicators, not partitions.  Partitions have numbers, like "sda1" (for the first partition on the "sda" drive), "sda2" (for the second partition ...), etc.

You most certainly don't want to mess around with merging drives.

You sure you don't have two 120GB drives in the PC?

---

### Post by yunone on 2013-07-10
its a laptop with SSD so i am assuming its one drive with two partitions. I am not sure how Windows would have formatted as such, but if its actually two SSD memory slots acting as two drives, that would be a surprise and make no sense. I was hoping its two partitions and for some reason its not letting me use the total space.

---

### Post by coffeecat on 2013-07-10
There are laptops - some Sony Vaios included - that come with two physical hard drives which are sometimes set up as a RAID. What is the model of Vaio? Perhaps you could google the specification and let us know.

Also - if you are running Gparted from the Ubuntu live session, open a terminal and post the output of:

```
sudo fdisk -lu
```

---

