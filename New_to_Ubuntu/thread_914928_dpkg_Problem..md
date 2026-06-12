---
title: "dpkg Problem."
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Breandean on 2008-09-09
I have a problem with dpkg,

"brendan@brendan-desktop:~$  sudo apt-get install nvidia-xconfig
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
brendan@brendan-desktop:~$ "

Also in add/remove programs, there is a bug I am asked to report about dpkg.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


Can this be fixed or should I reconfigure?

---

### Post by Rocket2DMn on 2008-09-09
Open a terminal and run
```
sudo dpkg --configure -a
```
This is required when a package manager is interrupted.

---

### Post by roger_1960 on 2008-09-09
Hi

Have had this as well. For me the manual configure suggested ie

dpkg --configure -a

fixed it. (both issues)

---

