---
title: "migrating computers using external and ubuntu"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by ntrgc89 on 2011-10-06
Hi all,

So I just got a new computer, and I want to move all my files/settings/etc straight from the old one to the new one, so it's like I just upgraded computers.

I thought about doing this using an ubuntu liveCD and my external hard drive. The idea being that I will boot into ubuntu on the old computer, copy the contents of the internal hard drive onto the external, then boot into ubuntu on the new computer and copy the files from the external onto the internal.

I was wondering, will this work? I wonder if there are settings that might not carry over and could mess up the new computer? Perhaps registry values might get tricky?

Any insight would be greatly appreciated, thanks!

---

### Post by Frogs Hair on 2011-10-06
Take a look at this program .[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ntrgc89 on 2011-10-06
Hm, very cool, thanks for pointing that out.

I wonder how clonezilla deals with partitions? i.e. my current hard drive has a 30GB windows partition, and a 50GB data parition. The new hard drive is 350GB. Will clonezilla repartition the new drive to match what it copied, or will it copy the 30gb and 50gb paritions separately?

---

### Post by Mark Phelps on 2011-10-07
I've not actually used Clonezilla to "clone" drives, only use it to image partitions, but from what I've read, if you do "clone" your existing drive onto a new one, it copies the sectors from one drive to another.  Your new drive will then have exactly the same stuff on it as your old drive, meaning, the partitions will be the same size and same postitions.

Then, when you connect the new drive, it should start up OK -- but you will then have to boot from a CD (Ubuntu LiveCD or GParted LiveCD) to resize the partitions because you can't change partitions that are in use.

Also, you mentioned "registry settings".  If by this, you mean you're also trying to migrate an MS Windows install to another PC -- most likely, that's NOT going to work.  Why? because the current install has the drivers for the current hardware.  When you boot this drive in a different PC, the drivers won't work -- and it probably won't start.

---

### Post by ntrgc89 on 2011-10-07
> **Mark Phelps said:**
> Then, when you connect the new drive, it should start up OK -- but you will then have to boot from a CD (Ubuntu LiveCD or GParted LiveCD) to resize the partitions because you can't change partitions that are in use.

Also, you mentioned "registry settings".  If by this, you mean you're also trying to migrate an MS Windows install to another PC -- most likely, that's NOT going to work.  Why? because the current install has the drivers for the current hardware.  When you boot this drive in a different PC, the drivers won't work -- and it probably won't start.

So it will copy the partitions, but it wont? I'm a bit confused as to why I have to resize the partitions after it's cloned, but that's more or less trvial, I'll be able to figure that out myself at some point.

As for drivers, I thought windows might automatically recognize that there is new hardware and apply some default drivers until I can get the real ones in, or will it simply not start up as it's waiting for hardware that's not there?

---

### Post by audiomick on 2011-10-07
> **ntrgc89 said:**
>  why I have to resize the partitions after it's cloned,

The assumption is that the new computer has a bigger drive than the old one. The cloned image will only take up as much space as is on the old drive, so it is logical that you will then want to expand the partitions to fill the new drive.

> 
As for drivers, I thought windows might automatically recognize that there is new hardware...

From what I know of windows from Vista onwards, when it recognises that the hardware has changed, it decides that it has been pirated and refuses to work. This is,however, not an expert opinion.

---

