---
title: "Can't edit /etc/modules and  /etc/modprobe.d/aliases."
date: 2008-07-10
forum: Philippine Team
---

### Post by adredz on 2008-07-10
when i try to edit /etc/modules i get this error:
 
 adred@adred-desktop:~/Desktop$ sudo kate /etc/modules
 Error: "/var/tmp/kdecache-adred" is owned by uid 1000 instead of uid 0.
 Error: "/tmp/kde-adred" is owned by uid 1000 instead of uid 0.
 Error: "/tmp/ksocket-adred" is owned by uid 1000 instead of uid 0.
 
 same thing happens when editing aliases:
 
 adred@adred-desktop:~/Desktop$ sudo kate /etc/modprobe.d/aliases
 Error: "/var/tmp/kdecache-adred" is owned by uid 1000 instead of uid 0.
 Error: "/tmp/kde-adred" is owned by uid 1000 instead of uid 0.
 Error: "/tmp/ksocket-adred" is owned by uid 1000 instead of uid 0.
 
 what should i do?

---

### Post by loell on 2008-07-10
maybe it's just kate? 

try **nano** editor

---

### Post by ajgreeny on 2008-07-10
Don't know if it will make any difference, but it should be ```
kdesu kate file/name
``` not sudo, which is just for non gui utilities and applications, not for kde or gnome apps.  kde should always use **kdesu** and gnome should use **gksudo**

---

### Post by adredz on 2008-07-10
thanks! :)

---

