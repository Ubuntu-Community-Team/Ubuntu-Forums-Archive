---
title: "having a hard time installing themes"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by enri2 on 2008-11-12
this is very confusing ...all the themes when i install give a error:
"**** does not appear to be a valid theme." 
then i tried installing aurora engine and it was only 40kb lol .deb. installed fine but i didn't see anything  on the themes, well this is weird ...

---

### Post by Therion on 2008-11-12
Well, first off an engine is not a theme, in and of itself; it's the software that allows you to implement certain themes that require that particular engine. 

What theme or themes, specifically, are you trying to install and where are you getting them from?

---

### Post by enri2 on 2008-11-12
[http://techwizrd.deviantart.com/art/Blue-Synth-102405482](http://techwizrd.deviantart.com/art/Blue-Synth-102405482)
this theme

---

### Post by Therion on 2008-11-12
Mmmmkay... Well first off it's .gz file.  It's my understanding that .gz files SHOULD import into your themes manager without any problem.  You're dragging and dropping the downloaded .gz file onto your Theme Manager, correct; and that's when you're getting the error message?

In reading the commments you'll need to install the Aurora Engine AND Pixbuf:```
sudo apt-get install gtk-engines-pixbuf
```Do that, then try reinstalling the theme and see if it works then.  I have my doubts, but try it.

You might do better hunting for themes over on [Gnome Look dot org](http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100).  Most everything you'll find there will be drag and drop.

---

### Post by enri2 on 2008-11-12
> **Therion said:**
> Mmmmkay... Well first off it's .gz file.  It's my understanding that .gz files SHOULD import into your themes manager without any problem.  You're dragging and dropping the downloaded .gz file onto your Theme Manager, correct; and that's when you're getting the error message?

In reading the commments you'll need to install the Aurora Engine AND Pixbuf:```
sudo apt-get install gtk-engines-pixbuf
```Do that, then try reinstalling the theme and see if it works then.  I have my doubts, but try it.

You might do better hunting for themes over on [Gnome Look dot org](http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100).  Most everything you'll find there will be drag and drop.
in the terminal didn't work , then i googled it and i found out that is already installed ... s*** i really need this theme...

---

