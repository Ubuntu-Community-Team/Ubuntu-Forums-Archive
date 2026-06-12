---
title: "GParted issue"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Ponhovo on 2008-07-22
i got only one HD in which is installed a ubuntu
if i resize this partition /dev/sda1 and create another as /dev/sda3, other than swap, which is already in there as /dev/sda2, am i going to lose everything?
if not, so, i can backup my home directory at sda1 to sda3 after resizing and applying in GParted and, then, reinstall ubuntu in sda1?

---

### Post by Helios1276 on 2008-07-22
Whats the new partition for? If you can back up everything why not just start from scratch,that way you can plan exactly how you want things. Partition and seemingly re-partitioning takes a LONG time and can have it's errors. I recently had to downsize my / partition a little to increase my boot, it went without a hitch but took an entire day to complete, which is probably less time then a format and fresh install in retrospect lol.

---

### Post by northern lights on 2008-07-22
> **Ponhovo said:**
> if i resize this partition /dev/sda1 and create another as /dev/sda3, other than swap, which is already in there as /dev/sda2, am i going to lose everything?
Why would you? In an unlikely case such as the electricity going during partitioning for instance, you might lose "everything". Otherwise: nope, that's fairly safe.

> **Ponhovo said:**
> i can backup my home directory at sda1 to sda3 after resizing and applying in GParted and, then, reinstall ubuntu in sda1? Pretty much. Just don't expect your system to be exactly the same, it might still require some tweaking, depending on how much you had altered in the first place. Everything that's stored in your /home directory will not only be kept, but integrated in the new installation right away, if, during setup you choose to make sda3 your /home.

---

### Post by Ponhovo on 2008-07-22
nonono...
i wud backup, yeah
but backup in a partition that doesnt exists yet, the sda3

can i rely that no electricity problem will make me lose my data? whats the probability that somthing like that wud happen?

sda3 wont be my home, i want to format sda1 and install a new ubuntu in there
but backup the files theres still in there to sda3, that doesnt exist yet. 

so i wud resize sda1 and create sda3 [sda2 is swap], then backup the data from sda1 of the new small size to that sda3, then format sda1, install ubuntu in sda1 and boot it with all my backup in the other partition, sda3

got it?

there`s no other way i wud backup here, coz i got no money for a external HD and its 71GB of backup, i wudnt buy so many DVD`s to burn :tongue:

---

### Post by northern lights on 2008-07-22
Fair enough, you can copy it back to sda1 also, same thing. I did get it, I think, in the first place. Simply suggesting, since you might have to do this again sometime down the road, you might as well keep a separate /home...

---

### Post by Ponhovo on 2008-07-22
so, no way i wud lose anything of sda1, other than the little probability of falling a lightning down in my HD or myself, or, while formating and resizing, a logical error occur and mess the damn thing up?

---

### Post by thschiavo on 2008-07-22
Seems so. I always do that, for me and for some friends. But I always suggest backing everything up before anything is done, just because there is a non-vanishing probability... This is a security perform, not a necessary one.

Anyway, if you try it, please post the result.

---

### Post by theLonghorn27 on 2008-07-22
always back up... especially if you upgrade to hardy.

---

### Post by northern lights on 2008-07-23
Moving his /home to the supposed-to-be-created sda3 - what is that other than a backup?

---

### Post by Ponhovo on 2008-07-23
already said i cant backup if sda3 doesnt exist before resizing 

well
i resized and everything gone fine
no data lose and no lightning =D

---

