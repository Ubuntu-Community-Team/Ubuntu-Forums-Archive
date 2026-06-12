---
title: "Wierd Icon on my Screen"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by ceil210 on 2012-10-07
This red icon.... It showed up after i upgraded to ubuntu 12.04LTS; I can't figure out how to ditch it.  It seems to be a notification thing.



**Edit:  **I clicked and read and this is what I found.
> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: BrokenCount>0'.  This usually means that your installed packages have unset dependencies.I am still at a loss

---

### Post by hydn79 on 2012-10-07
Have you tried what the output told you to do? :)

If you have "synaptic package manager" installed, use it to manually purge all broken dependencies.

Also try:
```
sudo apt-get autoremove

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ceil210 on 2012-10-07
Yes I did:

> E: /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.2_i386.deb: conffile './etc/xdg/Trolltech.conf' is not in sync with other instances of the same package
**Edit:  **  Fixed by deleting the stuffs

---

