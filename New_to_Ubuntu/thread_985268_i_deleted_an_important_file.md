---
title: "i deleted an important file"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by groo128 on 2008-11-17
that's it. while installing lua i erased by mistake /usr/bin/ld
How could i get it back?

Thank you in advance!

---

### Post by SamNSane on 2008-11-17
I believe that "ld" is part of wine. If you have wine installed, you could just reinstall it from within Synaptic. I'm assuming that's where you got wine in the first place. If you downloaded and compiled it for your system, you may have to go about fixing this in a slightly more complicated way.

---

### Post by philinux on 2008-11-17
Is it not in the trash.

If not here's one from my system. or find out whence it came and reinstall the app.

---

### Post by sisco311 on 2008-11-17
try:
```
sudo aptitude reinstall binutils
```

---

### Post by groo128 on 2008-11-17
thank you all, it's fixed :)
wise guys!!

---

### Post by sisco311 on 2008-11-17
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

