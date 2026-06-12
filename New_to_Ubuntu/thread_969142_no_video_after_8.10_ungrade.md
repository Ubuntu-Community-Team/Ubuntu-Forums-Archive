---
title: "no video after 8.10 ungrade"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by crazypenguin2008 on 2008-11-03
after the upgrade to intrepid video in youtube stoped working...any ideas on how to fix this?? :(

---

### Post by Tom--d on 2008-11-03
Install Flash since its not installed by default due to licencing issues.

From the command line (quick).
```
sudo apt-get install flashplugin-nonfree
```

Or its in Add/Remove.

---

### Post by crazypenguin2008 on 2008-11-03
it spit this back out at me  


crazypenguin@crazypenguin-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for crazypenguin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
crazypenguin@crazypenguin-laptop:~$

---

