---
title: "Problems with &quot;make&quot;."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by jorgeguberte on 2008-08-31
I've downloaded this program: [http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)
everything went okay, until the "make" command. 
Here's the yield:

make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

What can be done?

---

### Post by fedex1993 on 2008-09-01
you might need to make those directyls or you need to use qmake.conf. If you don't install build-essential

---

### Post by jorgeguberte on 2008-09-01
> **fedex1993 said:**
> you might need to make those directyls or you need to use qmake.conf. If you don't install build-essential

and how can i do that? ^^

---

### Post by Oldsoldier2003 on 2008-09-01
```
sudo apt-get install build-essential
```

---

### Post by jorgeguberte on 2008-09-01
> **Oldsoldier2003 said:**
> ```
sudo apt-get install build-essential
```

i got this:

```
build-essential is already the newest version.
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 239 not upgraded.

```

is there an "easy way" to install the 4fl? Flash is one of the things i use more oftenly, since i work with graphic design, so, i really³ need to install it, and i want to install it under Ubuntu. :)

---

