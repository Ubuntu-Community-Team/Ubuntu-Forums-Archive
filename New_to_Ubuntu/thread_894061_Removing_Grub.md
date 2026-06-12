---
title: "Removing Grub"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by tysonh on 2008-08-18
HI,

I just booted from a live cd and used gparted to nuke my ubuntu partitions and resize my xp partition to cover the whole drive.  I had the laptop dual booted with windows xp.  It worked fine but I need more space for school work.  How do I remove grub and use the windows boot loader?  When I restart and begin to boot the drive.  It loads grub then stops and says error 22.  Where normally it would give me the option to pick which OS I wanted to use.  I figured since ubuntu was no longer on the driver grub wouldn't be either.

So in short I just to get rid of grub so I can boot windows.  If this won't work is my only option to format and reinstall?

---

### Post by tysonh on 2008-08-18
can I fix it with a fixmbr command in the recovery console of windows?

---

### Post by aheckler on 2008-08-18
> **tysonh said:**
> can I fix it with a fixmbr command in the recovery console of windows?

Yes.

---

### Post by arpanaut on 2008-08-18
That should work, but if not...
Give this a shot:  [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

