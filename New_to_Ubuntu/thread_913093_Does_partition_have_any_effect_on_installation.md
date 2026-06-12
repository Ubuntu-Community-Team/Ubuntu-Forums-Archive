---
title: "Does partition have any effect on installation?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-09-07
I got two Samsung hd502ij where I have Win installed one the first one and are trying to install ubuntu on the secound, question is if it have any effect what partition I install ubuntu on?

---

### Post by The Cog on 2008-09-07
The easiest thing to do is to delete the partition you want to install Ubuntu on, then tell the installer to install into the free space. On top of it being simpler that way, the installer knows to create two partitions in the space - a system partition and a small swap partition, and knows what filesystem formats are required.

---

### Post by SpinningAround on 2008-09-07
> **The Cog said:**
> The easiest thing to do is to delete the partition you want to install Ubuntu on, then tell the installer to install into the free space. On top of it being simpler that way, the installer knows to create two partitions in the space - a system partition and a small swap partition, and knows what filesystem formats are required.

I actually have a little space one the harddrive that win isn't on the problem is that I can't seem to get it to auto partition it, is there some special command or?

It look like this
Hdd1 - Winxp
hdd2 - free space | ntfs

---

