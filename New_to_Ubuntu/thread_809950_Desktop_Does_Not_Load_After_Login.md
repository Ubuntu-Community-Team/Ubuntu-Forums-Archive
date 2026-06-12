---
title: "Desktop Does Not Load After Login"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Stoolcat on 2008-05-27
So I installed Ubuntu 8.04, and I set my username and password during the install.  I then try to login using these, and it says incorrect username/ password or whatever.  I alt+ctrl+f2 and change my password.  Now when i login, it plays what I imagine is the bootup sound, kind of a jungle beat, and my screen goes blank.  My monitor pops up "no signal", which means that it is not getting a signal, then the nice beige screen loads and the login screen loads quickly afterwards.

So I guess I'm stuck.  Any help would be greatly appreciated, and I will respond quickly if more information is needed.

---

### Post by spiderbatdad on 2008-05-27
Could you post some spec regarding your computer, and the type of install, ie. wubi, clean install, dual boot...?

---

### Post by Delever on 2008-05-27
From sessions, choose Failsafe GNOME and try again. This will load failsafe session from which you can use System->Administration->Hardware drivers to install/enable restricted hardware drivers, if they are needed. If that is not the case, we will need more info.

---

### Post by Stoolcat on 2008-05-27
I am dual booting with windows XP.
I will try the sessions thing, so I'll give that a try and come back with results.

---

### Post by iaculallad on 2008-05-27
If you could drop in your terminal, try re-installing the desktop instead :)


Code:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Stoolcat on 2008-05-27
well, I am posting from within Ubuntu =)
I used the failsafe gnome option, so that worked... but Umm  I dont know what you mean by enable restricted hardware drivers.

THe only hardware driver that is listed is an ATI accelerated graphics driver, which is ¨not in use¨

---

