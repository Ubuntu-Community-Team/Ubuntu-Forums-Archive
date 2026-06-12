---
title: "Increase memory"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Sofoklis on 2012-06-21
Hello! 
My laptop has both Linux(ubuntu) and Windows. I want to increase the amount of memory for Linux. How do i do that (without losing any information/files from my windows memory)?

---

### Post by raja.genupula on 2012-06-21
use this for more information [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mark Phelps on 2012-06-21
> **Sofoklis said:**
> Hello! 
My laptop has both Linux(ubuntu) and Windows. I want to increase the amount of memory for Linux. How do i do that (without losing any information/files from my windows memory)?

Memory is NOT disk space.

IF you're asking about disk space, and your PC is running Win7, do NOT use GParted to shrink Win7.  Doing so risks corrupting Win7 and rendering it unbootable.  Instead, use the Win7 Disk Management utility to do the shrinkage.

---

### Post by raja.genupula on 2012-06-22
> **Mark Phelps said:**
> Memory is NOT disk space.

IF you're asking about disk space, and your PC is running Win7, do NOT use GParted to shrink Win7.  Doing so risks corrupting Win7 and rendering it unbootable.  Instead, use the Win7 Disk Management utility to do the shrinkage.

+1  and my link will be helpful to you if you have other Partition which are storing data of yours and not belonging to windows 7 partition .

---

### Post by mastablasta on 2012-06-22
i hope it's not a wubi install...
 
otherwise ddefragment, run checkdisk (chkdsk) and then reduce partition size with windows disk management tool.

---

