---
title: "[SOLVED] Help with Screenlets"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by DFord425 on 2008-08-29
I installed screenlets, or so i think. When i goto start it, a window comes up then disapears. Does anyone know what might be wrong, sorry i know its not much info but if there is anything i should do to troubleshoot, let me know. Thanks

---

### Post by Crafty Kisses on 2008-08-29
Not sure if you're using KDE 4.1 but that has built in Widgets already.

---

### Post by vikramaditya on 2008-08-29
install dbus-x11 package that contains dbus-launch

see [this]("http://forum.compiz-fusion.org/showthread.php?t=4781&page=2") and read post #14

---

### Post by DFord425 on 2008-08-29
how do i figure out which version kde i have?

---

### Post by DFord425 on 2008-08-29
> **vikramaditya said:**
> install dbus-x11 package that contains dbus-launch

see [this]("http://forum.compiz-fusion.org/showthread.php?t=4781&page=2") and read post #14

Thanks, that worked.

---

### Post by vikramaditya on 2008-08-29
open "kerminal" (or whatever the hell terminal is called in kde) and type
```
cat /etc/issue
```
Hit enter key and it should reveal all. :)

---

### Post by vikramaditya on 2008-08-29
> **DFord425 said:**
> Thanks, that worked.
Outstanding!  But, thank Google...not me.  And, be sure to mark this thread **Solved**  :)

---

