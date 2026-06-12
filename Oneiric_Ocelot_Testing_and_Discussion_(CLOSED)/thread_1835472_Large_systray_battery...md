---
title: "Large systray battery.."
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by weverall on 2011-08-29
I upgraded to 11.10 and when i log in i have this large Systray image of a battery which i think is the battery indicator from 11.04 but i cant find out how to get rid of it?

---

### Post by fjgaude on 2011-08-29
I wouldn't call what you did an upgrade as Oneiric is still in Alpha testing, very changeable! I can't say what happens with Natty being 'updated' into an Alpha version of Oneiric. Sorry!

---

### Post by cariboo on 2011-08-29
never mind.

---

### Post by althu on 2011-08-30
If you had any chance to allow all indicators to show in panel, try to revert to the default. That was my case.

Run dconf-editor, look up "desktop - unity - panel", and set systray-whitelist to the default. Or use gsettings command.

---

