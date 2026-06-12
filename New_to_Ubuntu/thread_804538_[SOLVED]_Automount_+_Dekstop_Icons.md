---
title: "[SOLVED] Automount + Dekstop Icons"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-23
My USB devices mount fine, but I can't get them to display an icon on the dekstop, how can i do this??

---

### Post by sdennie on 2008-05-23
Maybe you've somehow turned off that functionality.  Start gconf-editor and go to /apps/nautilus/desktop.  You'll see some options there that might help.  Specifically, turning on "volumes_visible".

---

### Post by Yanluo on 2008-05-23
Another option is if you have installed gTweakUI. The nautilus app there has an option to remove icons. If you have not marked the "Use nautilus to draw desktop", then mark it and icons will appear (hopefully).


EDIT: Typo

---

### Post by takuhii on 2008-05-26
> **vor said:**
> Maybe you've somehow turned off that functionality.  Start gconf-editor and go to /apps/nautilus/desktop.  You'll see some options there that might help.  Specifically, turning on "volumes_visible".

that worked a treat, thanks!!

---

