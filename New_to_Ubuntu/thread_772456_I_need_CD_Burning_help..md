---
title: "I need CD Burning help."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Deathbeholdsyou on 2008-04-28
Question 1.
What do I burn as? Image? or the other one?
Because I want to make a redistribute CD of Hardy
I'm assuming Image
And, one more
Question 2.
When I put the 8.04 CD in, run through start up and all, and I come upon the "Partition" part of the CD Installation, on a Laptop hard drive, it has windows
It doesn't show the hard drive partitions like 7.10 did, it'd show all the partitions
and partition sizes.
Should I just downgrade to 7.10, or should I stay at 8.04 and wait to see if anything happens with the partitions?

---

### Post by szymon_g on 2008-04-28
1. if you wanna redistribute HH to your friends, you should burn those images as a 'bootable images', not as a ordinary data

2. i dont really understand whats the problem: it shows (afaik) all partitions on your hard disc. whats wrong with that?

---

### Post by oedha on 2008-04-28
1a.. can be copy CD ( if you want to distribute it in cd )
1b. when you do copy cd find an option tells "create image only" later you will have *.iso

2. have you shutdown the windows properly ? 
2a. di windows defrag at least two times
2b. manage your partition using [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by alienexplorers on 2008-04-28
1) If you have the .iso file then burn it as an image file.  If you only have the CD then use copy CD.

2) What exactly do you mean it does not show the partitions.  When I loaded 8.04 and got to the partition section it showed my windows partition and the free space I used to load Ubuntu 8.04.  I made 3 partitions in the free space and all went fine after that.

---

### Post by duckgoesoink on 2008-04-28
Mine didn't show the partitions either - try choosing the manual option and do it from there (create a little partition formatted as swap, and another bigger one formatted as ext3 - set to /). Be careful not to overwrite your Windows partition - it will show as NTFS.

---

