---
title: "HOWTO: Set Numlock on"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by jeremy on 2005-10-16
System setting -> Hardware -> Keyboard -> Numlock on KDE startup, select Turn on.

---

### Post by haaglin on 2005-10-23
If you want Numlock on before KDM, instead of after, you can do it like this:

#sudo apt-get install numlockx 

#sudo kwrite /etc/kde3/kdm/Xsetup

and add this at the end of the file:
```
/usr/bin/numlockx
```

This is how my Xsetup looks:
> 
#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &
/usr/bin/numlockx


---

