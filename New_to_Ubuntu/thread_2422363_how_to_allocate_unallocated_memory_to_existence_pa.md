---
title: "how to allocate unallocated memory to existence partition"
date: 2019-07-06
forum: New to Ubuntu
---

### Post by pratap73 on 2019-07-06
how to allocate unallocated memory to existence partition

---

### Post by Impavidus on 2019-07-06
There are two things you can do. You can extend the existing partition to the left to get one big partition, or you can create a new partition in the empty space and mount it somewhere convenient. Most of us are not particularly fond of a very large partition containing both the OS and all user data.

The quick solution is to make one big partition (not really recommended). As your sda6 is a logical partition inside your sda2 (the extended partition), you have to shrink sda6 before you can shrink sda2 and you have to extend sda2 before you can extend sda6. Furthermore, you cannot change a partition that's currently in use, so you have to do this using a live disk.

The better solution is to put your OS in a 30GB partition and use the remainder of your hard drive for a data partition or a /home partition. There are several ways to do this, not terribly hard, but the fastest way is to make a fresh install. It's your choice.

In any case, before you change any partition, make sure you've got current backups of all files you don't want to lose on an external, disconnected drive. Almost everything that can go wrong during partitioning will lead to data loss.

---

