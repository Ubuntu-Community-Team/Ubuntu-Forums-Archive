---
title: "How to close wine?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-05-25
Does wine slow up my computer?

How do I close it after I'm though using a program that needs it?

---

### Post by h4mx0r on 2008-05-25
You exit out of it like any other program. However if something crashes you can do the command wineserver -k to close out anything that is running.

---

### Post by Barrucadu on 2008-05-25
When you close all programs running through WINE, WINE closes.

---

### Post by misfitpierce on 2008-05-25
Indeed so lets say you were playing Full Tilt Poker like myself through Wine. Simply hit the X to exit program and BAM! Wine and Full Tilt go bye bye :)

---

### Post by niceguy123 on 2008-05-25
I ran Pisaca under wine, close Pisaca, but still see wine on my desktop and bottom toolbar. See attach sreenshot.

---

### Post by niceguy123 on 2008-05-25
Sorry, posted twice and couldn't figure out how to delete the 2nd one.

---

### Post by saj0577 on 2008-05-25
```
xkill 
```
then click it.
OR 
```
pkill wine 
```
might/should work.

Saj

---

