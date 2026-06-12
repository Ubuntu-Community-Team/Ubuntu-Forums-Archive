---
title: "Partioning hangs up before 0%"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Robert98374 on 2008-11-12
For some reason when i am trying to partition my hard drive so that Ubuntu will have 100gs of my 320g machine it just freezes up on the partition wizard. I have let it sit for about 30 mins and there is no progress. Should i try and redownload Ubuntu again?

---

### Post by Keen101 on 2008-11-12
don't know what to tell you.  Try doing a disk integrity check to see if the disk has problems. If it checks out, then try this instead.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by prshah on 2008-11-12
> **Robert98374 said:**
> when i am trying to partition my hard drive so that Ubuntu will have 100gs of my 320g machine it just freezes up on the partition wizard. 

If you're also running Vista, most people suggest using Vista's disk manager instead of linux's gparted to free up space.

If you're trying to modify existing partitions, they will have to be unmounted first, so essentially, you will have to use the partition tool from the live CD, rather than your installed system. Remember to turn off swap from the live CD's partition editor before making any partition changes! (Right-click swap partition in partition editor / gparted and select the option "swapoff".) 

If you find any other partitions that have a "lock" icon next to them, right click them and select "Unmount".

---

### Post by Robert98374 on 2008-11-12
How do you access Vistas Disk manager?

---

### Post by prshah on 2008-11-12
> **Robert98374 said:**
> How do you access Vistas Disk manager?

Start-Run```
diskmgmt.msc
```

(OK Actually, that's in XP, but should work in Vista as well!)

---

