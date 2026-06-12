---
title: "How do i install ubuntu and erase my old XP OS?"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by paulezy on 2013-01-31
so i got this nice clean desk top PC Dell Pentium 4 3.2 ghz 2.49 gb ram running windows XP. How where and what do I need to install a Linux operating system on it? I do not want the XP OS on this computer. i downloaded Ubuntu 12.10 and it partitioned the drive and doesnt ask me to format or get rid of the old OS. I tried to Format through the command prompt and it wouldnt let me. any suggestions?

---

### Post by elgordodude on 2013-01-31
Welcome to the forum,

Burn a proper install cd, you can use XP for this purpose, then install from that. The partitioning process will ask you about disk structure during the install process, but not to the extent that it did in say 10.04. You can also delete and reformat your hard drive using gparted on the live cd. On a side note, I've had better success with 12.04 on legacy (aka P4 hardware) than 12.10, you may want to consider it on a fresh install to avoid future problems.

---

### Post by deadflowr on 2013-01-31
If you're installing from the default install disk from Ubuntu, then choose the option to install over the whole disk.

It's been a while, but from memory:

1) Install side by side with existing operating system 
this allows for a dual-boot)

2)Install on the whole disk. (This wipes the disk and automagically repartitions it for an Ubuntu install; it also makes a swap partition and sets the mbr)

3)something else. (this is the one to manually set partitioning schemes, Unless you know what's what I don't recommend this one, as one missed step can through you for quite a loop.

---

