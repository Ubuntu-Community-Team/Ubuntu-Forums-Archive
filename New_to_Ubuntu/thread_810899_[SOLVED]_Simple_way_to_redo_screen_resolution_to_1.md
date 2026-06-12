---
title: "[SOLVED] Simple way to redo screen resolution to 1024X768?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-28
There is a since reconfigure xserver command I know to reconfigure the screen resolution, my question is what needs to be done to make it perminately stay @ 1024X768?

---

### Post by zvacet on 2008-05-28
**System>preferences>screen resolution**

---

### Post by sports fan Matt on 2008-05-28
i forgot to add that im in failsafe gnome, though, i cant boot into the gnome cause the screen was funly, i was trying to remember the command to auto set it like reconfigure xserver.xorg or something

---

### Post by LarryJ2 on 2008-05-28
> i was trying to remember the command to auto set it like reconfigure xserver.xorg or something 

Maybe this is what you are trying to recall?

 sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by sports fan Matt on 2008-05-28
I reset gnome issue solved :)

---

