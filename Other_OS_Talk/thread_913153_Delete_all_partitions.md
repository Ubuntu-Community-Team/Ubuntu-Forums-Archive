---
title: "Delete all partitions"
date: 2008-09-07
forum: Other OS Talk
---

### Post by Viridia on 2008-09-07
OK, so I tried a bunch of Linux distros. One kinda exploded on me and created a bunch of partitions. I want to know how to delete all the partitions on my HDD, and just have one big partition. It would be especially handy if someone knew how to do this in Wolvix, but I an use another Live CD if absolutely neccessary. 

Thanks

---

### Post by cdtech on 2008-09-07
Using the Live CD when it gets to the desktop just open "gparted" and you can manipulate all the partitions.

---

### Post by smoker on 2008-09-07
you can do this with gparted, which i believe is on the ubuntu live-cd, or you can download from the repository. never used wolvix, but you may get it from their repository, if not already on the cd.

you can also download and burn gparted on it's own from here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Viridia on 2008-09-07
Ok, I'm not sure how to use it...

What would I do to merge all of my partitions together? And in what format should I make it (fat32, ext3, etc;)

Thanks

---

### Post by cdtech on 2008-09-07
Once your in the gparted program you can just remove all partitions which will give you a complete unallocated space then just use the entire space to create a partition and format to your taste. Using the Live CD to install Ubuntu you could format to ext3.

---

### Post by LaRoza on 2008-09-07
> **Viridia said:**
> Ok, I'm not sure how to use it...

What would I do to merge all of my partitions together? And in what format should I make it (fat32, ext3, etc;)

Thanks

You would delete them all (or all but one) and make one big one (or make make the one take up all the extra space).

What format depends on what you plan to do with it. If you plan on using it with Linux distros, ext3 would be a good choice. If you plan on using it with Windows, leaving it unformatted and allowed Windows to format it is the best.

For anything else, let us know.

---

### Post by Viridia on 2008-09-07
Ok, so I would look at all the partitions, delete them all, and create one new one that is 30 GB in size (my HDD is 30 gigs.)

Thanks

---

### Post by Viridia on 2008-09-07
Oh, two of my partitions are locked. How would I go about unlocking them?

---

### Post by cdtech on 2008-09-07
Yes sir, that's correct..

Good luck.

---

### Post by LaRoza on 2008-09-07
> **Viridia said:**
> Oh, two of my partitions are locked. How would I go about unlocking them?

Why are they locked? Are you using a live disk? If you are using an installed Linux to do this, you can't edit mounted partitions.

---

### Post by Viridia on 2008-09-07
> **LaRoza said:**
> Why are they locked? Are you using a live disk? If you are using an installed Linux to do this, you can't edit mounted partitions.

I fixed it, I thought I was booting from a Live CD, evidently not. I had to set some boot parameters first.

---

