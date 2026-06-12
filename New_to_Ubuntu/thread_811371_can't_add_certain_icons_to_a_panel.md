---
title: "can't add certain icons to a panel"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by nick_jones on 2008-05-29
when i try to add cetain icons (trash, labtop battery were a couple i noticed) i get an error message and i can't add them to the panel, any ideas what's going on?

another little problem, everytime i restart, my bottom panel go to the top of the screen and it wont let me put it back to the bottom, i wind up deleting the panel and creating it all over again, it get annoying

here's a screen of my error message:

---

### Post by SunnyRabbiera on 2008-05-29
What version does this occur in?

---

### Post by nick_jones on 2008-05-29
hardy

---

### Post by wdaniels on 2008-05-29
I can't say I have much idea about specifically what might be wrong here, but my best guess would be that something is broken in your gnome configuration data. I would create a new user, log in with it and see if you have the same problems with adding stuff to the panel.

---

### Post by nick_jones on 2008-06-04
> **wdaniels said:**
> I can't say I have much idea about specifically what might be wrong here, but my best guess would be that something is broken in your gnome configuration data. I would create a new user, log in with it and see if you have the same problems with adding stuff to the panel.

yeah, same problem. the first thing that happened when i logged on to the new use account was "The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"" error

---

### Post by forestpixie on 2008-06-04
Bit long winded but the only way I managed to get the trash back on a panle was to put it on the desktop and drag from there

Use gconf-editor - then apps - nautilus - desktop - trash icon visible

---

