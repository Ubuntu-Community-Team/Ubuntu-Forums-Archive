---
title: "Eliminating GUI Login"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by chromatic.glissando on 2008-10-09
Ok...I first got acquainted with linux on a really old laptop with an old version of Red Hat Linux installed. I kind of liked having the terminal login screen...

Is there any way I can get a terminal login screen (no GUI), without sacrificing the automatic boot into GNOME? I'm still kind of unfamiliar with writing boot scripts and such...but is a boot script that loads GNOME after a lower init level is entered a possibility? Or can I edit the init levels in some way for a similar purpose?

Thanks :)

---

### Post by Gregmond on 2008-10-10
Not sure what you are trying to do, if you want to ignore the gui login and just login to a terminal, try Ctrl+Alt+Fx where x = 2 to 7 (F7 is back to the gui), so Ctrl+Alt+F2 will give a different terminal session to Ctrl+Alt+F3.

---

### Post by iponeverything on 2008-10-10
Goto:

System -> Administration -> Services

and turn off GDM

---

