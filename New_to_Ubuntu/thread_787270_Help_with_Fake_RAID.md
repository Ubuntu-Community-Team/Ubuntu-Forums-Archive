---
title: "Help with Fake RAID"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by niplfsh on 2008-05-08
Hey all, I finally bit the bullet and put Ubuntu on my main rig, not just one of the random boxes I have laying around.  I have a 74gb Raptor which is split into three partitions: XP, Ubuntu, and one for experiments (I'm playing with OSX86 atm).  Ubuntu sees all of these partitions fine. But I cannot get my RAID array to register.  It's a 2x320gb RAID 0, controlled by the ICH7R on my intel Bad Axe.  It's in NTFS and all my data are on it. 

I've read about dmraid, and it gives me this:
```

jw@456:~$ sudo dmraid -ay
RAID set "isw_bffehbbgeg_Big Momma" already active

```

...so it SEES the array, but it isn't showing up anywhere.  I don't know where to go from here; the tutorials I've found involve formatting and repartitioning the array, which is not something I want to do.  
Thanks in advance
JW

---

