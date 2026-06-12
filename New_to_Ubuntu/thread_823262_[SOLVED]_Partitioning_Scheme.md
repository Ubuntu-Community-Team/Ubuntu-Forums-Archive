---
title: "[SOLVED] Partitioning Scheme"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-09
I have a 60g hard drive in my laptop.  I have to use half of it for school.  I want to make the other half the current ubuntu.  I have the cd I need to install it, I just need to know what the partitioning scheme should be.

Everytime I've tried the automatic default scheme the install hangs at 15%.  I'm hoping that someone could show me what partitions to make and what sizes to make them assuming that the ubuntu install is only going to use 30g's.

And yes Im sure there are about 10,000 how to's out there for dual booting and believe me I've tried them.  I'm tired of using gparted to start over because something im doing isn't right.  Please help!

---

### Post by Xiong Chiamiov on 2008-06-09
You need at minimum 2 partitions: one is swap space, one is everything else.  There are some who recommend multiple partitions (/home on separate one, for example), but I find that I need the flexibility over the slight security (and other) benefits.

The general rule of thumb used to be to make a swap partition twice as big as your RAM.  I have 2 gigs in my system, and I never touch my swap (which is 1 gig).  I'd say making them combined to be 2 gigs, but there is room for adjustment, depending on how many memory-intensive applications you tend to run.
That partition will be of file-type "swap".

The other parition will take the rest of the free space.  You want the file-type to be "ext3", and the mount point "/" (root).

I'm sorry, I'm not the best at explaining installs, but you did ask for personal help as opposed to the many well-written guides out there.

---

### Post by tysonh on 2008-06-09
Thanks for the help xi.  I don't know what swap was even used for so any help at this point is great.  Does swap just act like additional memory?

---

