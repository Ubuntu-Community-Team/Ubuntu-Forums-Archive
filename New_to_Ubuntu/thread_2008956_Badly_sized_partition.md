---
title: "Badly sized partition"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by sanderella on 2012-06-23
When I installed 12.04 I made a poor decision about how much space to allocate to it on my hard drive. I left Windows installed, and only allocated 30% of my drive to Ubuntu.

Is there any way of altering this without re-installing?

---

### Post by blackbird34 on 2012-06-23
If you want to give more space to Ubuntu, you can shrink the Windows ( C: or whatever /dev/sd** its on) partition when logged in to Windows with the corresponding disk utility (whatever the name is). 
Then you boot into a Ubuntu liveCD ("try ubuntu") in order to use GParted to enlarge the Ubuntu partition and that's it. 

As GParted always says, do a backup before manipulating partitions on the off chance something goes wrong...

---

### Post by Mark Phelps on 2012-06-23
When you installed, did you do it from INSIDE Windows? If so, it is not in a separate partition.

---

### Post by audiomick on 2012-06-23
+1 that

Do backup. Something could go wrong, like a power failure or something else beyond your control. Gparted could probably do  the resize without a problem, but there is a Windows tool for working on Windows partitions, so it seems sensible to me to use the tool that the manufacturer provides.

Making notes of partitions names and sizes as you go is not a bad idea either. ;)

---

### Post by sanderella on 2012-06-24
Thank you, will try this.

---

