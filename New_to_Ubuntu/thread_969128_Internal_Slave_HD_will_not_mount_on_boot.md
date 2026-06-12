---
title: "Internal Slave HD will not mount on boot"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-03
I just did a fresh install of 8.10 (was running the beta, but for unrelated reasons, had to start from scratch).  My system includes a 160 gb master and 320 gb slave drive.  I'm running a dual boot with XP.

So, previously, running 8.10 beta, I booted up, logged on, and any drives that were in the system appeared on the desktop, ready to access with full read/write permission.

Since installing the new release, external drives show up, but my internal slave does not.  If I go to Places, Computer, it's there.  I can double click on it, and the password screen pops up, I enter my password, then receive some error message about no mount point for the selected object - cannot mount it (something like that).  I dismiss that error message, and can then double click on the drive and it works normally - also then appears on the desktop.

What would be causing this and how do I fix it.

BTW, instead of double clicking, I can also right click, choose mount, and go through the remaining steps above (including error message) to get the drive working.

This happens with every restart.

Advice appreciated.

Caruso

---

### Post by taurus on 2008-11-03
You need to add an entry in /etc/fstab if you want it to mount automatically each time you boot Ubuntu.  Maybe this thread would give you an idea.

[http://ubuntuforums.org/showthread.php?t=968270](http://ubuntuforums.org/showthread.php?t=968270)

---

