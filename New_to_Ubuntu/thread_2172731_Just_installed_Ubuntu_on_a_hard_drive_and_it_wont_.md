---
title: "Just installed Ubuntu on a hard drive and it wont boot"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-06
I just installed Ubuntu 12.04 PP on one of the three hard drives I have in my PC.  I chose / as the mount and made the whole 1gb partition ext4.  When I choose to boot the hard drive in BIOS, it just boots my other hard drive that has Windows 7 on it.  I know I installed it because I've installed Ubuntu from the same DVD, and it said the installation was complete.

What can I do to get Ubuntu to boot?

---

### Post by Mark Phelps on 2013-09-06
If you installed GRUB to the Ubuntu drive, you have to boot from THAT drive, not the Win7 drive.  You would have to change your drive order in the BIOS settings to put the Ubuntu drive first in the list.

---

### Post by TheFu on 2013-09-06
1G isn't enough storage to install any normal version of Ubuntu.  Are you sure that is the amount of storage you setup?
8G is sorta the minimal useful install for a desktop and 15G-20G would be recommended for / partitions.

If you really meant to say 1TB - a common mistake that we all have made - check my signature for **boot-repair** links.

---

### Post by ImTroyMiller on 2013-09-06
Yeah, I meant 1tb, not 1gb.

I'll try my repair disk and redo GRUB.  I have a feeling that may be the issue.

---

