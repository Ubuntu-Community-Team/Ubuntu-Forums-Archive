---
title: "Recently, Nautilus Auto Launches at @ Bootup - How 2 Remove?"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by GregA on 2012-06-25
Hello All,

In the past 2-3 weeks, Nautilus has appeared on my desktop upon startup.   I don't recall any change that prompted that.

Generally, I use Dolphin on this KDE system, and I prefer to start that myself as needed.  

How do I suppress the automatic startup of Nautilus?

Note, I've looked into the "Startup & Shutdown" manager in KDE, and I don't see a command to start Nautilus, although I do see a script called "gtk2-default-theme.rc.sh" in the Autostart tab (or view).   Could that script be responsible for Nautilus startup?   How do I find out what this script does?

Thanks,

Greg

---

### Post by GregA on 2012-06-25
OK, I checked the Process Manager application, and noted Nautilus was still active as a zombie.  Once I killed it, that solved the problem.   I can see when several people use 1 machine, it's important to close all apps -before someone else closes the active session.

---

