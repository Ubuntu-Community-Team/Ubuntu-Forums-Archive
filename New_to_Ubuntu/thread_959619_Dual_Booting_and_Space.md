---
title: "Dual Booting and Space"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by arthew on 2008-10-26
I want to dual boot XP Pro and Ubuntu on my machine. Can I use two seperate physical, not logical, hard drives or do the programs need to be on the same physical drive that is partitioned? I will be reformating my drives so how much space should I give Ubuntu to run comfortably? At this point I am trying Linux, it will not be my main OS, but I am more serious than to just run it from a CD.

---

### Post by dracayr on 2008-10-26
you can use different physical partitions. you can even put ubuntu on an usb drive.

Ubuntu needs about 2GB space (If I recall correctly). so, I would say not less than 5GB. It also depends on the programs you want to install

dracayr

---

### Post by bpowell2005 on 2008-10-26
> **arthew said:**
> I want to dual boot XP Pro and Ubuntu on my machine. Can I use two seperate physical, not logical, hard drives or do the programs need to be on the same physical drive that is partitioned? I will be reformating my drives so how much space should I give Ubuntu to run comfortably? At this point I am trying Linux, it will not be my main OS, but I am more serious than to just run it from a CD.

I set up an existing Windows machine to boot Windows off of the primary drive, and (optionally) boot Ubuntu off of a second physical drive. Both operating systems work just fine.

I have a virtual Ubuntu installation I use for testing / validation, and it ran out of space quickly with just 5 gig allocated to it...I currently have 15 gig allocated to it, and it's running just fine now...so I wouldn't go less than 15 Gig...you need room to install programs and play around!

---

### Post by Elfy on 2008-10-26
The recommended minimum is 4Gb - I have about 15Gb in total and have used about 8Gb in total - that said all my data is kept on seperate partitions, bear in mind the need for a swap partition.

You can install them on seperate drives - ubuntu will read your windows files if needed and vice versa.

Install windows first and all the updates it needs before you install ubuntu.

---

### Post by SunnyRabbiera on 2008-10-26
Well depending on how big your hard drive is sometimes a dual boot isnt worth it.
If you are running at 20GB of space, its not worth your time.
30GB is fair but because of the demands of windows and the average user the best dual boot can be achieved at over 40GB

---

### Post by ubername on 2008-10-26
It is also quite a good idea to have a / (boot) partition of say 10 Gb and a /home partition of whatever you like, but at least 10 GB I suppose, for all your user data etc. The partition manager on the CD lets you set them up. I didn't bother when I first started using Ubuntu but now I find it really useful as you can do a clean install of the OS from a CD without trashing your user data.

---

