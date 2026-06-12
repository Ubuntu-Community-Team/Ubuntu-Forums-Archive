---
title: "error message in upate manager"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by catniko on 2008-11-30
Hello.  I  was wondering if anyone good tell me how to run: dpkg --configure -a in terminal.

I interupted the Update Manager as it was downloading while turning off my computer, now when I make an attempt to update, I get this error message:

E: dpkg was interrupted, you must manually run ' --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thank you.
--Kristin

---

### Post by drs305 on 2008-11-30
Open a terminal (Applications, Accessories, Terminal)

You must use sudo:
```
sudo dpkg --configure -a
```

You will have to enter your password and you won't see it as you type. Hit ENTER once you have typed it.

---

### Post by Shwefty on 2008-11-30
Open up Terminal by Applications -> Accessories -> Terminal

Then type:
```
sudo dpkg --configure -a
```

It'll then prompt you for your password.

---

### Post by Mud.Knee.Havoc on 2008-11-30
Question posed 3 minutes ago... two (correct) answers posted one minute ago... this is what I love about this forum! \\:D/

---

