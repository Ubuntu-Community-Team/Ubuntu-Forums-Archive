---
title: "Invisible Partitions."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by ubersquiz on 2008-06-03
Ok I have a tiny 80.gig hdd im using until my 500gig sata arrives alas my last drive died...anyhow lol.

I have windows installed as well as ubuntu 8.04 hardy heron with a dual boot.
Now the thing is I wanted to increase the size of the partition ubuntu is held on because i'm using it more than I was using windows. 

When I went into partition magic inside windows, the partition with ubuntu doesn't show up, its as if its not there, its just more free space. And the same is true when I try to look at the partitions in ubuntu, no sign of a windows partition anywhere. 

Unless i'm missing something and ubuntu uses a totally different method of partitioning that i'm not aware of i'm not really sure whats up. 
I tried using "sudo fdisk -l" to view all the partitions and it only shows one ?

Any help would be greatly appreciated.

(off topic, i LOVE ubuntu so far, its the only distro ive ever used that actually works and is now coming very close to making me scrap winblows alltogether :D)

---

### Post by sayakb on 2008-06-03
Try the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Boot into this LiveCD and resize the partition using GParted.

---

### Post by ubersquiz on 2008-06-03
Ah ha, many thanks i'll give that a go now :D

---

### Post by prshah on 2008-06-03
> **ubersquiz said:**
> 
I tried using "sudo fdisk -l" to view all the partitions and it only shows one ?


Can you please post the output?

---

