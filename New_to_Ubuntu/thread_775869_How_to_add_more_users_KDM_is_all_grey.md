---
title: "How to add more users KDM is all grey"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Kenobi on 2008-04-30
After I installed Kubuntu 804 KDE4 with 1 user I can't set up more users! The only place to do so is in the system settings (Login Manager), but it stays grey and you cant click a thing!

Could you please check out if Login Manager works for you? Anyone the same problem?

---

### Post by beartard on 2008-04-30
There are a lot of configuration utilities that haven't made it into KDE4 yet.  Is it the only environment you have installed?  You could always use kcontrol in KDE3.  Other than that, there's always the old-fashioned command line tool "adduser".  It will prompt you for all the information you'd have to fill out in KDE's user settings.

---

### Post by Kenobi on 2008-04-30
Hi,

thanks for you fast answer, beartard! But I found out more now. 

After an excessive search on where on earth the system settings are stored on the drive, I tried to start it as sudo. Now I could edit all the information that was *greyed out* earlier.

Obviously the developpers forgot a button to enable the user to get temporary root rights!

---

### Post by beartard on 2008-04-30
Hehe.  Yeah, there is that.  It's always something simple.  Well most of the time.  Ok, sometimes.  Alright, it sux all the time.

Btw, be sure and use "kdesudo" or "kdesu" instead of "sudo" when you load gui apps.

---

