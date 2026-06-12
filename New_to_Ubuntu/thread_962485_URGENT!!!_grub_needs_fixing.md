---
title: "URGENT!!! grub needs fixing"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by rkakkar on 2008-10-29
i want to remove ubuntu and i have removed all my non-windows partitions through the live cd's gparted. unfortunately i forgot to fix grub before doing so and now my windows isn't loading. how can i fix it?

---

### Post by eddietours on 2008-10-29
just make sure with gparted that theres no swap in front of the windows partition

---

### Post by tompickles on 2008-10-29
Boot from your windows disk and enter into the recovery mode and run 'fixmbr'. That will reinstall the windows boot loader.

---

### Post by rkakkar on 2008-10-29
i can't enter windows! and my windows disk straight away loads windows setup.

---

### Post by philinux on 2008-10-29
If your windows disk wont do it then get this to fix your windows mbr.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

And yes it does fix windows mbr's

---

### Post by caljohnsmith on 2008-10-29
Go to the "recovery console" on your Windows Install CD by typing "r" at the first main menu you get, and as tompickles said, run:
```
fixmbr

```

---

### Post by tompickles on 2008-10-29
Typically, on an XP disk you have to read the screens a lot, and then hit 'R'. Vista on the other hand there is a small inobvious recovery console option after you select your langauge etc

---

### Post by tarps87 on 2008-10-29
The windows install cd should allow you to enter a recovery mode then then fix the mbr as suggested above. This is defiantly the case with XP and Vista, which version of windows are you using?

> **eddietours said:**
> just make sure with gparted that theres no swap in front of the windows partition
This won't change anything, the swap partition is used to paging which is a form of memory management (there is a swap file rather than partition in Windows) It is the mbr (Master boot record) which will be on the bootable partition that need setting to use the windows bootloader rather than GRUB

---

