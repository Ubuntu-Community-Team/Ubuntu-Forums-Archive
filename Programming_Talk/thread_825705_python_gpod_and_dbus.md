---
title: "python gpod and dbus"
date: 2008-06-11
forum: Programming Talk
---

### Post by soxs on 2008-06-11
Can anyone give me valid information about the python modules gpod and dbus. I am going to put my 2c in exailes iPod plugin... (I just started programming python..)

---

### Post by soxs on 2008-06-11
Bump.
Does anyone know about how amarok detects iPod/iPod model and all that stuff?

---

### Post by imdano on 2008-06-11
The best way would be to look at the source code for Amarok's iPod plugin and find out for yourself.  Also, you shouldn't need dbus at all to add on to the ipod plugin in Exaile.  What are you going to use it for?

---

### Post by soxs on 2008-06-12
I am going to dynamically detect ipod connection and if that is a to big task for a newbie like me, I will at least try to get the ipod mountpoint on ipod connect.
Amarok is all in cpp and the ipodplugin does not really mess with detecting, just about write/edit/delete content from the ipod :-S (at least as far as I understood, I may have missed something in the 2500 lines of cpp code)

---

