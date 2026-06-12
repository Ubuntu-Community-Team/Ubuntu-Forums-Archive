---
title: "[SOLVED] Synaptic/apt-get/Add-Remove/etc. all broken--KDE's fault"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by fiddler616 on 2008-08-15
Hello,
A few days ago, I realized Ubuntu was running too smoothly, and installed kubuntu-desktop, just for a change of pace. I didn't like KDE, and removed it. It seemed to go all right, but apparently kio-unmount wrapper did not get uninstalled, instead breaking, and now Synaptic, Add-Remove, apt-get etc. all don't work since kio-unmount wrapper is broken. I've tried removing it, but can't. I can paste in errors if you guys want.
I also saw [https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/186729)
which seems to be the problem, but none of the workarounds work.
So all help is appreciated
(PS--I'm sorta new to this, so if I should go whine to the bug report instead of this thread, let me know)
Thanks in advance.

---

### Post by fiddler616 on 2008-08-15
Don't ask me why, but now everything works. I don't even know what I did.
Huh.

---

### Post by rockerphil on 2008-08-15
first thing that pops to mind to do is to run this

sudo dpkg --configure -a

that should fix any problems if the dpkg process was interupted, then i'd try to uninstall kio-unmount with

sudo apt-get remove -y --purge kio-unmount

if that doesn't work please post the results here, and if i can't help i'm sure someone else can :)

Phil

---

### Post by rockerphil on 2008-08-15
well, glad ya got the problem sorted, please remember to mark your thread as solved

Phil

---

