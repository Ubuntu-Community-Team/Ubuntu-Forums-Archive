---
title: "Shout Out!"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by MrWES on 2008-05-19
Just felt a need to shout out that I just installed two gigs of new mem and Gusty is flying high now! heh..

Is there a way to reclaim the gig partition I have at /swap ?

Thanks for listening,
Bill

---

### Post by wolfen69 on 2008-05-19
resize your ubuntu partition with [GPartedLiveCD]("http://gparted.sourceforge.net/livecd.php")

---

### Post by bluefrog on 2008-05-19
turn the swap off (swapoff)
format the swap partition as ext3
edit /etc/fstab and change the swap line according to the new mount point which will be used for the new partition.

Alternatively forget about it.

---

