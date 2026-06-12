---
title: "Install Ubuntu over Windows ?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by clipeuh on 2008-07-16
I have two partitions: C: with windows on it and D: with my music and other stuff.
How can I install Ubuntu on C: ?
I don't want Dual-Boot.

---

### Post by Elfy on 2008-07-16
When you run the installer it will give you options when you get to the partition part.,

see below

Partition numbering is different here.

---

### Post by mevets on 2008-07-16
You need a way to distinguish the two partitions when you boot the liveCD and get to the partitioning part. The easiest way to do this is to know how big the C: drive is. So, when you get to the partitioner you will both drives but you will know which one is which because you know how big the C drive is. With the C drive identified, you should use the paritioner to mark this parition to mount at the / (root) mount point.

---

### Post by appi2012 on 2008-07-16
do you have a ubuntu live cd? if so, boot into it and run terminal (Application -> Accesories -> Terminal) and type:
```
sudo fdisk -l
```

Which of your partitions is bigger, music or C:/

Go to System -> Administration -> Partition Editor, and then delete the partition the is your C: partion (figure out by checking whether it is bigger or smaller than the other.

then hit install, and use the "Guided - use the largest continuous free space" option

Using the "use whole disk option" as suggested above, will wipe all your partitions.

---

### Post by Elfy on 2008-07-16
> **appi2012 said:**
> Using the "use whole disk option" as suggested above, will wipe all your partitions.

catch - I thought it would give option as to which partition. I use manual method,

---

