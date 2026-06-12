---
title: "is there any way of partioning hard drive while mounted"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by hazman on 2008-05-13
is there any way of partioning my hard drive while mounted.reason i'm asking is i have a low spec lappy that works in ubuntu but a bit sluggish so was concidering partioning hard drive and trying dsl or puppy linux.problem being i have no bootable media no floppy and my external cd-rom is not bootable and carn't get it to work

---

### Post by JoshuaRL on 2008-05-13
> **hazman said:**
> is there any way of partioning my hard drive while mounted.reason i'm asking is i have a low spec lappy that works in ubuntu but a bit sluggish so was concidering partioning hard drive and trying dsl or puppy linux.problem being i have no bootable media no floppy and my external cd-rom is not bootable and carn't get it to work

Unfortunately no.  You can't partition a hard drive that's currently mounted.  Sorry.

---

### Post by Oldsoldier2003 on 2008-05-13
You cannot manipulate mounted partitions because of the risk of data damage, the partitioner needs exclusive access to the partition. If you have two partitions you could unmount the non system partition and work with it.

If you have the ability to boot from USB you could use [gparted live usb]("http://gparted.sourceforge.net/liveusb.php") to resize your partitions..

---

### Post by hazman on 2008-05-13
so am proverbably up a stream without a paddle.its not that i dislike ubuntu i think its ace just need a bit of speed thanks any

---

### Post by mapes12 on 2008-05-13
So how did you install Ubuntu onto your HDD in the first place? If you can run a CD on your lappy to install Ubuntu then you should be able to run a GParted CD via BIOS to set partitions.

---

