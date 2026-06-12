---
title: "Boot Failure in 8.10"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by wangsacl on 2008-11-25
Just recently, I upgrade my 8.04 hardy to 8.10 intrepid.
Well, while upgrading, I fell asleep.
And now, when I'm going to check my laptop back again (yes, the laptop is turned on for almost 24 h), after i'm logging in, the ubuntu's desktop won't show up! These things happened in all kernel, from 2.6.27-7, 2.6.24-21, and 2.6.24-19.
How to fix this failure?
FYI, after I'm checking the recovery mode on the most recent kernel, there's a terminal that I can use.
By typing apt-get update, the terminal says that dpkg is interrupted. But, after checking it by typing dpkg --configure -a, the terminal says that dpkg won't configure anything.
Please help me in fixing these things. Thank You.

---

### Post by bumanie on 2008-11-25
You need to do that as root > sudo dpkg --configure -aSee how that goes.

---

### Post by wangsacl on 2008-11-25
It's the same.
FYI, the terminal recognize the user as root (root@ivan-laptop) so, we don't need any sudo.

FYI, when I run the dpkg, there are some message such as:
dependency problems - leaving unconfigured
Package * is not configured yet.

---

### Post by bumanie on 2008-11-25
You may have to do a fresh installation. Most upgrades work well, but there are a number of threads on this forum with issues such as yours, thus upgrading via update manager is not perfect. I believe Canonical provide a warning stating that there is a chance that the upgrade process may break your system. Unfortunately, it looks as though that may have happened with you. I have a separate / and separate /home and always do a fresh install to /

---

