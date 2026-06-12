---
title: "where is xorg.conf?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by mills on 2008-06-15
can someone remind me where xorg.conf is please

---

### Post by Nepherte on 2008-06-15
/etc/X11/xorg.conf is the full path.

---

### Post by aktiwers on 2008-06-15
aktiwers@HAL:~$ locate xorg.conf
/etc/X11/xorg.conf

---

### Post by mills on 2008-06-15
aghhhh locate command

i tried find and whereis but nothing, forgot about locate
havent been usin linux much lately

thanks all

---

### Post by mrsteveman1 on 2008-06-15
Locate works most of the time unless the database is missing or out of date. You can always use the find command:

```
find / -name xorg.conf
```


For binaries you can use the which command:

```
steves-mac-mini:~ steve$ which java
/usr/bin/java

```

---

### Post by sujoy on 2008-06-15
just update the locate database with

sudo updatedb


locate works great.

---

### Post by the_doc on 2008-06-15
Or run it as a cron job then you won't have to worry about it.

---

### Post by Joeb454 on 2008-06-15
> **the_doc said:**
> Or run it as a cron job then you won't have to worry about it.

It depends how often you're going to use the tracker, or "locate" really :p

I hardly ever use it, I have some strange file organization, but it works :) I usually remember where stuff is

---

### Post by oldos2er on 2008-06-15
> **mills said:**
> can someone remind me where xorg.conf is please

 Your subject title nearly had it right, type "whereis xorg.conf" in a terminal.

---

### Post by aktiwers on 2008-06-15
> **oldos2er said:**
> Your subject title nearly had it right, type "whereis xorg.conf" in a terminal.
That will not return the location of xorg.conf, rather just xorg. the locate on the other hand will return the full path of xorg.conf.

> aktiwers@HAL:~$ whereis xorg.conf
xorg: /usr/lib/xorg
aktiwers@HAL:~$ locate xorg.conf
/etc/X11/xorg.conf
/etc/X11/xorg.conf.backup
/etc/X11/xorg.conf~
/usr/share/displayconfig-gtk/xorg.conf.fallback
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
aktiwers@HAL:~$ 

---

### Post by oldos2er on 2008-06-15
So it does. Thanks!

---

