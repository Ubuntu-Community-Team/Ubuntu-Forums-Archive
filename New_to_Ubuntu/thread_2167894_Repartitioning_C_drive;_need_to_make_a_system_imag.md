---
title: "Repartitioning C drive; need to make a system image"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by androideka31 on 2013-08-15
Hello all, I've been running Precise Pangolin since January, and it's great. The only problem I'm now having is I'm running out of space (found out when trying to dl Android Studio). I want to keep all of my stuff without having to manually reinstall, etc. Is there a way I can create a system image so I can store it externally and then repartition my drive (thinking about removing Windows completely, thoughts?). Any ideas?

Thanks.
Love, 
androideka31

---

### Post by Petro Dawg on 2013-08-15
If you have no worries about losing windows, you could use gparted to delete your windows partition and then grow your linux partition without having to reinstall (unless you do something wrong).  You might also have to reinstall grub (but thats not too difficult).  

Alternatively you could try to shrink your Windows partition (from within windows) and then use gparted to expand your linux partition.  I've personally done this in the past without issue.

---

### Post by androideka31 on 2013-08-15
Cool. I still have some things to backup from my Windows partition, but I'll let you know how it goes.

---

