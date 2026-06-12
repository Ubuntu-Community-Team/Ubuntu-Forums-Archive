---
title: "Need to check if HD is ok"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by seepage87 on 2008-08-11
I recently had 2 disks on my array crash at once.  I actually think it was the south bridge that was the problem, so I would like to thoroughly check the disks for errors.  What's the best tools/methods to do this?  It's for my server, so CLI is better, I guess.

---

### Post by Crafty Kisses on 2008-08-11
> **seepage87 said:**
> I recently had 2 disks on my array crash at once.  I actually think it was the south bridge that was the problem, so I would like to thoroughly check the disks for errors.  What's the best tools/methods to do this?  It's for my server, so CLI is better, I guess.

You can check your HD for erros by doing the following:
```
sudo fsck.-t vfat /dev/hdbX
```
Replace the X at the end with the partition number.

---

### Post by jonabyte on 2008-08-11
try:

```
fsck --help
```

to see options you may want to run.

---

### Post by seepage87 on 2008-08-11
It's probably worth noting that these drives are still formatted to work in the RAID5, though they're technically "failed spares" right now.  I'm going to eventually put them back in an array, but in the mean time is the best course of action to format them to something else and run fsck?  Or is there something that would allow me to check for actual physical errors or something?

---

