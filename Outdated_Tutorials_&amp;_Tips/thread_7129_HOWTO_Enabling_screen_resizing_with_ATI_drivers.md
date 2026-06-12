---
title: "HOWTO: Enabling screen resizing with ATI drivers"
date: 2004-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by easy_target on 2004-12-04
You installed ATI drivers and now you aren't able to resize your screen under GNOME, right?
NO PROBLEMO!!!! 

Run sudo fglrxconfig and follow the questions (remember to point your mouse to /dev/input/mice ). When it asks you about XFree DGA choose NO!

You will be able to resize your screen again. ATI drivers don't get along every well with that feature. 

BONUS: If you use wine and your system hangs when trying to run a windows application, use the winesetuptk tool and deselect DGA also, and BINGO!!!
You're ready to go!!!

---

### Post by wallijonn on 2004-12-31
Nice tip. Maybe Matth can incorporate it into his HOWTO FAQ.

---

### Post by Fittersman on 2006-11-13
i get this:

```
cleippi@cleippi-desktop:~$ sudo fglrxconfig
sudo: fglrxconfig: command not found

```

and how do i use the winesetuptk thing?

---

### Post by TLE on 2006-11-14
[QUOTE=Fittersman;1750828]i get this:

```
cleippi@cleippi-desktop:~$ sudo fglrxconfig
sudo: fglrxconfig: command not found

```

Then you probably need to install the fglrx-control package:
```
sudo apt-get install fglrx-control
```

---

