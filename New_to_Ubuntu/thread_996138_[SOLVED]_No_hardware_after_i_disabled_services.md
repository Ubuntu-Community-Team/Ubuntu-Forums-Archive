---
title: "[SOLVED] No hardware after i disabled services"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by prafjessor on 2008-11-28
So i tried to speed up boot time by disabling some services. I used the services device under System/Administration/Services and a program called bootupmanager. I know now it was stupid, but i thought i knew what i was doing. The problem now is nothing works. No keyboard, no mouse, nothing. There is a window on the desktop saying something like /failed to initilaze hal/ but i cant close it or do anything, cause the keyboard isnt working. Is there a way to undo this?

I would very much appreciate help! Im writing this off a live cd.

---

### Post by skymera on 2008-11-28
Which did you untick?

Did you disable one called "system communication bus" ?

---

### Post by prafjessor on 2008-11-28
> **skymera said:**
> Which did you untick?

Did you disable one called "system communication bus" ?

Oh man, i dont know. Maybe. I googled alot and came up with **/etc/init.d/hal start**, but when i write it in recovery mode nothing happens. it just says something like are your dbus running?

---

### Post by skymera on 2008-11-28
ok thought it was dbus. That has to be enabled.

ok go to console or a tty screen and type

```
 sudo /etc/init.d/dbus start 
```

Then type ```
 startx 
```

Go to System > Admin > Services and retick the dbus (System communication (Very bottom))

---

### Post by prafjessor on 2008-11-28
> **skymera said:**
> ok thought it was dbus. That has to be enabled.

ok go to console or a tty screen and type

```
 sudo /etc/init.d/dbus start 
```

Then type ```
 startx 
```

Go to System > Admin > Services and retick the dbus (System communication (Very bottom))

Thank you very much, it worked. I learned my lesson!

---

