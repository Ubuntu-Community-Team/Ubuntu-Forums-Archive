---
title: "cant install plugin"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by derek89 on 2008-10-30
Im completely new to this im trying to install swfdec plugin for mozilla and i keep getting this message 


"E:dpkg was interrupted,you must run 'dkpg --configure -a' to correct the problem


E:_cache->open() failed please report"



could someone please help me

---

### Post by nothingspecial on 2008-10-30
Do what it says, type

```
sudo dkpg --configure -a
```

---

### Post by nothingspecial on 2008-10-30
You spelt it wrong - it`s dpkg not dkpg

---

### Post by derek89 on 2008-10-30
thanks but this dont help i dont know what to do from here i tried going to the website and download the plugin but when i go to install it it says a conflicting program is running but i dont have any programs running but it hasnt worked right since yesterday when i lost power installing limewire please i dont mean to sound stupid but thats kinda how i feel right now

---

### Post by Zalbor on 2008-10-30
You said this doesn't help, but not why. Try entering the above command (with dpkg instead of dkpg) in a terminal (Applications>Accessories>Terminal) and if the problem isn't fixed, copy the output from the terminal and post it here.

---

