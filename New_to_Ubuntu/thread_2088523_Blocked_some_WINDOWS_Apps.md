---
title: "Blocked some WINDOWS Apps"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by turnbub on 2012-11-26
My hard drive is partitioned:-  C: for my WINDOWS OS and basic software,  D: for "other" apps, and E: for data.
Not a lot of point to separating out the apps, but the data on E: is a good idea, methinks - easy to back up data that way.

More to the point - my harddrive is plenty big so I added a partition at the end, called it X: tried to install UBUNTU there but couldn't seem to make it work, so I let UBUNTU just do it's own thing.

Well, UBUNTU created another partition within the space allocated as D:, the "APPS" partition.  The partition program in WINDOWS recognizes C: D: *: (where UBUNTU is), and E:

My data is still fine on E:, however, WINDOWS cannot access the APPS in D:

I still have to try and fix the problem, failing which I can scrub the whole thing and restore my drive from a backup taken before I installed UBUNTU (YUP, I believe PC Magazine when they said to do this!)

Would welcome any suggestions, but mainly putting this experience out there in case it helps anyone else.

---

### Post by newb85 on 2012-11-26
It's really refreshing to hear that someone actually backed up their stuff before diving in.  Restoring to that point and trying again is probably a good idea.

If you use the Windows installer (wubi), then Ubuntu isn't installed to a real partition--it's placed on a virtual partition (which is actually a file within one of your Windows partitions).  It sounds to me like this may be what you did.

Instead, I recommend downloading the appropriate .iso and using it to create a Live CD/DVD/USB and installing that way.  A normal install (not on a virtual partition) requires that the partition not be created by Windows.  Ubuntu needs to be installed on an Ext* partition (Ext4 is the newest and best), which Windows won't create.

Definitely defrag your Windows system before installing Ubuntu.

Also, if your machine uses MBR partitioning (most Win7 & older machines do), it's a good idea to make the fourth partition an Extended partition and place your Ubuntu partition(s) within that.  The reason for this is that MBR can only have four primary partitions, but you can put as many partitions as you want within an Extended partition.  Even if you only think you need four partitions now, creating that Extended partition can save you headaches down the road if you decide you want to add partition(s).

---

