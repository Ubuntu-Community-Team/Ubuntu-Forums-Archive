---
title: "What determines scsi or ide?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by rsnow on 2008-07-23
According to fdisk -l, my hard drives are scsi (sda, sdb). I have never knowingly configured a computer to have scsi drives. This machine is several years old and as far as I know it was always 2 hard drives on an ide cable and operated under windows as ide. What caused the change or did I do it unwittingly when I installed Ubuntu?

I would like to partition these drives to have 2 versions of Linux on drive 1 and 2 or 3 versions on drive 2. I don't plan on installing that many right now but down the line I would like to look at different versions without doing a lot of un-installs or installing over top of an installed version. What is easiest to use for partitioning, gparted or something else?

---

### Post by PinkFloyd102489 on 2008-07-23
The drive in my server used to be hda when I had Dapper on it. Now it's sda with Hardy on it. Dunno what changed but it really doesnt bother me.

---

### Post by jordanmthomas on 2008-07-23
A recent change in the kernel makes all hard drives show up as sdX now.

---

### Post by rivera151 on 2008-07-23
> **PinkFloyd102489 said:**
> The drive in my server used to be hda when I had Dapper on it. Now it's sda with Hardy on it. Dunno what changed but it really doesnt bother me.

Yes, somewhere around 2.6.20 the ide driver was changed to use the scsi driver instead for reasons I still don't understand.  But any ide drives will show up as scsi devices (sdaX).

---

### Post by rsnow on 2008-07-23
Well, that explains that. Thanks for the info. No, it doesn't really bother me as much as I was just curious. Back when I first started messing with computers the "geeks" of that era were always talking about their scsi configurations as if they were beyond us mere mortals.

I figure as long as it works.....

---

