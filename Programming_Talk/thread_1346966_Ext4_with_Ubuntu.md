---
title: "Ext4 with Ubuntu"
date: 2009-12-05
forum: Programming Talk
---

### Post by phillw on 2009-12-05
Hi folks :-)

I was having a read about ext4 from the people over at [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

And I came across this. It troubles me.
Should I go with the ubuntu blkid library, or should I use the volid library, as they > *highly* recommended

> **  For people who are running Ubuntu **

 Ubuntu 9.04 and later include ext4 as a manual partitioning option at installation time, including support for ext4 as the root filesystem. 
For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available [here]("ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/ubuntu-fixed-util-linux").   These packages revert a [change made by Ubuntu]("http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.12r-19ubuntu1/changelog") to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this decision for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found [here]("ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/ubuntu-fixed-util-linux/util-linux-patch"). 
 

Many thanks,

Phill.

---

### Post by phillw on 2009-12-08
(bump)

---

### Post by falconindy on 2009-12-08
Karmic drops vol_id and uses blkid instead.

---

