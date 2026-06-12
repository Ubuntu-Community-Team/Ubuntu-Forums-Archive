---
title: "Partitioning"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by RickFAA on 2013-05-18
I have one 320GB hard drive in a desktop.  With Dual Boot.
One OS has Vista(!) ~130GB (/dev/sda1,2,3 with all that *ell Util/Recover stuff).

One OS has Ubuntu 12.04 ~128GB
 (/dev/sda4 extended 5, /dev/sda5 115GB 83, /dev/sda6 83 OS 6GB and /dev/sda7 82 Swap 4GB).

Question:
Should my Ubuntu partitions be better like this:
(/dev/sda4 extended 5, /dev/sda5 83 OS 6GB, /dev/sda6 83 115GB and /dev/sda7 82 Swap 4GB). 

Or should I not change anything?  I though that the {OS} could be first, then the {DATA}, and the swap. 
And the OS has only 1.8GB unused....... BAD?

This is from my DVD copy installed last week. 

Thanks!
RickO

---

### Post by Paqman on 2013-05-18
> **RickFAA said:**
> 
Or should I not change anything?  I though that the {OS} could be first, then the {DATA}, and the swap. 


You might get a very small improvement in speed from doing this, but I'm not sure it would be worth the hassle to get it. Maybe do a fresh install when 13.10 comes out and modify it then. Your swap is probably much bigger than it needs to be. Swap needs to be the same size as RAM if you ever intend to use hibernation, otherwise 0.5-1Gb is plenty. Again, not a big difference, but you could claw back a little bit of space next time you reinstall.

> 
And the OS has only 1.8GB unused....... BAD?


Yes, this will result in fragmentation of the filesystem. In general you don't want to run any partition greater than about 80% full.

---

### Post by Impavidus on 2013-05-18
It's not yet at 80%, but if you install a few programs with large data directories you will get problems. Program data, in contrast to user data, goes on the OS partition by default. I don't think you'll miss two or three GB from your data partition.

---

