---
title: "Adding Launcher buttons to Panel"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by burtzacarach on 2008-08-09
Im trying to add shortcuts to my panel in Xfce, but I don't know where the image files for the programs I want to add are located.
Just things like Pidgin and Evolution, with icons, are what I'm looking for.
Help please?

---

### Post by mc4100 on 2008-08-09
It depends on your theme, however, you might try /usr/share/icons

For example, Evolution:
/usr/share/icons/Human/scalable/apps/evolution.svg

Edit: Hmmm, Pidgin seems to be in /usr/share/pixmaps
so try in there as well.

Edit, again ... OutOfReach beat me to it, lol.

---

### Post by OutOfReach on 2008-08-09
Well, you can also check in /usr/share/pixmaps

---

### Post by burtzacarach on 2008-08-09
Found the icons, thank you. 
But where are the image files for the programs I'm trying to make launchers for?

---

### Post by Seamyst on 2008-08-31
> **burtzacarach said:**
> Found the icons, thank you. 
But where are the image files for the programs I'm trying to make launchers for?

Assuming you know the name of the program you want, go to Applications >> Accessories >> Appfinder and search for the name of the program.  Right-click on the result and select More Information.  The text after "Command" is what you want; just type that into the appropriate field when you're adding a launcher.

---

