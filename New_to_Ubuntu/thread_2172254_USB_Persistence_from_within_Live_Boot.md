---
title: "USB Persistence from within Live Boot?"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by evamvid on 2013-09-04
Hey Everybody,

I used UNetBootin to make a LiveUSB the other day. After it crashed multiple times setting up persistence, I chose not to use persistence. Now, I have it booted up and running, I need to know if there is a way to make it persistent from within the LiveBoot session. In case it helps, I'm using Precise; 12.04.3, amd64, on a 4gb drive. 

Thanks!
--evamvid

---

### Post by JeQhdMD on 2013-09-04
Suggest you try "Startup Disk Creator" app which should come bundled with Ubuntu/Kubuntu, etc.  It seems to do a better job at creating persistence enabled USB based buntu's than unetbootin  . . . .

---

### Post by PaulW2U on 2013-09-04
> **evamvid said:**
> Hey Everybody,

I used UNetBootin to make a LiveUSB the other day.

I've never used it because....

> **JeQhdMD said:**
> Suggest you try "Startup Disk Creator"

....has been very reliable no matter what flavour of Ubuntu I've been using at the time.

The "persistence" mode worked just as it should apart from the one time I kept updating a development version with daily updates. But for remembering customisations and installing a few small applications it's been fine and worked as expected.

---

### Post by ian-weisser on 2013-09-04
> **evamvid said:**
> I need to know if there is a way to make it persistent from within the LiveBoot session

Not safely.
The USB stick must be repartitioned and overwritten.
If the write fails for any reason, your USB stick will be unbootable. And writes do fail.

---

### Post by evamvid on 2013-09-04
So I found out that the Universal USB creator lets you do persistence. I'm trying that.

I knew about the Startup Disk Creator, but I can't use it from a live-boot from the same drive. 

If I partition the drive, could it work? The problem is that I'm not sure I have enough space. Also, I wouldn't be able to use the rest of the partition that it is running off of. 

I think the easiest way to do this would be to use the startup disk creator running from a CD onto a USB. But, the only computer I'm able to boot onto has a broken disk drive (it sucks not having a disk drive). So I have to try to find one that works in Windows, at least for the time being. I think in a few weeks I'm going to be able to dual-boot Ubuntu with Windows...

Also, what happens if I set Universal USB Creator to 1 GB persistence, but I don't have a free GB? I noticed that on the current install, my drive (4GB) only had 377MB available.
Will it break the drive? Or will I only have 300MB of Persistence?

---

### Post by evamvid on 2013-09-05
Christmas has come early!

I was able to install 12.04.3 dual-boot on a computer last night!


Success!

Thanks, everyone, for your feedback...

I'm going to leave this post open for a couple more days, in case we find a solution to my previous problem that could help anyone else.

---

