---
title: "partition hp 2000-239dx"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by i8ajar on 2012-02-19
I'm trying to install ubuntu on my hp but hp puts the factory restore on one of the partitions, as the third of four primary partitions.  I'm not sure how to adjust the partitioning to add ubuntu.  Any help would be appreciated.

---

### Post by Bucky Ball on 2012-02-19
You can create an extended partition with your free space and that will count as one. You can then put as many *logical* partitions in that as you like. Ubuntu doesn't need to be on a primary partition so you can put these three logical partitions (drives):

/ = 20Gb
/home = as big as you like
/swap = 2Gb fine

... inside the extended one when you install Ubuntu. Problem solved. 

Your other option is to burn the restore CDs from the HP toolkit (or whatever it's called) so you can restore from these manually and wipe the lot. Up to you.

Good luck. ;)

---

### Post by i8ajar on 2012-02-24
Thanks I made a backup disk and deleted that partition. Then I made a new partition through windows and installed ubuntu on that partition. That worked fine so I appreciate the help.

---

### Post by Bucky Ball on 2012-02-24
Nice work! Enjoy! Don't forget to post back if you have any other issues. ;)

---

