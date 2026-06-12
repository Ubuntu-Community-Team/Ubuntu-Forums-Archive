---
title: "amarok plugin for Gnome music applet"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-11-15
Hi,
Is there anyway to make amarok plugin for gnome music applet work without the kdecore module. 

Thanq

---

### Post by prkos on 2009-01-22
I had the same message about amarok plugin in music applet

The expression "kdecore" might be a bit confusing, the actual package in question is python-kde3 (I had python-kde4 installed but amarok used kde3 so I had to install python-kde3 too). 

After I had that installed it asked for pcop, it's actually python-dcop package, I installed that and now music applet is working with amarok :)

---

### Post by khaelo on 2009-03-14
It worked!  Thank you.  :)

---

