---
title: "Recovering hard drive with gddrescue"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by Derk_Blade on 2014-12-15
I had a hard drive issue where the thing wasn't booting that I appear to have exacerbated by running fixboot from the winXP recovery console. I'm now attempting to make an image before proceeding further using an ubuntu liveusb and gddrescue. However, when I attempt to make an image, it seems to be stuck on retrying bad sectors with a message like this
 

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:         0 B,  errsize:  80000 MB,  current rate:        0 B/s
   ipos:     9771 MB,   errors:       1,    average rate:        0 B/s
   opos:     9771 MB,    time since last successful read:     1.6 h
Retrying bad sectors... Retry 1

I also tried using testdisk, but that simply informed me that there was a read error at every location

Is there some obvious thing I'm doing wrong? It seems like ddrescue simply can't read from the hard drive at all. I would appreciate any help or advice.

In case it's relevant, the drive in question is a Maxtor DiamondMax 10 80gb, Model:6L080M0

---

### Post by TheFu on 2014-12-16
Perhaps setting the  ddrescue retry value to a lower number would get it moving passed those bad areas quicker?  I've used it that why with almost failed disks.

If the entire drive cannot be read, no software will fix it.  **badblocks** is the normal way to locate ... er ... bad blocks on a disk. If there are too many that relocation isn't possible anymore, I don't know what happens.

Good luck.

---

### Post by kevdog on 2014-12-16
Well if you have another hard disk to copy to -- you could use the command dd to copy the entire drive to another medium.

---

### Post by TheFu on 2014-12-16
> **kevdog said:**
> Well if you have another hard disk to copy to -- you could use the command dd to copy the entire drive to another medium.

Actually, dd will hang/die on errors.  That's the primary reason to use ddrescue instead.

---

### Post by Derk_Blade on 2014-12-18
Quick update, swapped things around and the problem doesn't appear to be the cable, the power supply, or the computer I was testing it with. Since the software I'm poking it with all seem to report that the entire hard drive is one read error, I assume this means that there's some sort of hardware issue?

---

### Post by TheFu on 2014-12-18
So, at this point I need to ask - when was the last complete backup made?  Time to use that to recover data onto a new HDD.

If **badblocks** worked at anything, you may need something with an easier interface?  **Spinrite** is cheap, commercial, but cannot fix hardware issues. However, if there is any strange noises coming from the disk, best to turn it off and mail it to a professional ... 

Or - open your checking account and pay a professional to do their magic.  [http://www.myharddrivedied.com/](http://www.myharddrivedied.com/) - I've met Scott and he knows his stuff. Lots of videos and podcasts with him online.

I suppose you could try to get a used HDD with the exact same onboard electronics and attempt to swap that out yourself. I wouldn't, but many people can accomplish things I cannot.

Some people might say that I'm giving up too quickly. Fine.  My data is worth more than the computer. Once a HDD has shown **any issues at all**, I stop using it. Corrupt data just isn't worth the $150 for a new HDD to me.

---

