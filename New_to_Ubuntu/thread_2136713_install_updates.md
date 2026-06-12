---
title: "install updates"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by Calvinista on 2013-04-18
I installed ubuntu 12.10 last week using wubi to evaluate it for an upcoming embedded system project.
I keep getting requests to install system updates . . . ordinarily I would do this as a matter of course, but this list is rather long and I don't recogize 80% of the items that want to install or update.

Is there any downside to letting the software updater have its way?

Thanks

---

### Post by ibjsb4 on 2013-04-18
After a fresh install there will always be a large update.  And there should not be a downside to this, but one never knows for sure.  Myself, I always worry about kernel uppgrades.  IMO thats is going to be the most likely thing to cause a problem.  So I pick and choose when and what kernel I download with a package called Synaptic Package Manager.  Its in the software center, but here's the catch.  You can't install things until you do the first update.  Sooo ..  To get around that you could do a terminal update/upgrade.  Like I said though, this is just my (paranoid) opinion :)

---

### Post by Impavidus on 2013-04-18
The first update after installing contains all updates since the image for the install disk has been created, which is half a year ago now. It's generally save to install all those updates and even wise, as they fix some bugs and security issues. Kernel updates sometimes break something, especially some drivers, but the nice thing about kernel updates is that the old kernel isn't automatically uninstalled, so you can still boot if it doesn't work, using your old kernel.

---

### Post by ibjsb4 on 2013-04-18
Thanks Impavidus for clearing that kernel thing up.  I do not have the software center installed and thought it would remove old kernels.  My bad :)

---

### Post by Calvinista on 2013-04-18
Thanks!

---

### Post by grahammechanical on 2013-04-18
You can turn off notification of updates. System Setting>Software Sources>Updates. If we were using a computer without Internet connection we would not know of any updates at all. And we would not worry about it either.

Regards.

---

