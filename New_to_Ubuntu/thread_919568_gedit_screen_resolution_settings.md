---
title: "gedit screen resolution settings?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-14
So my resolution is shot out from something that I have know idea what, but my resolution is set at 680x490 (not reaLLY but something wrong like that) my real resolution is supposed to be 1024x780 or ssomething like that.  This is not listed as an option in the resolution dialog box or nvidia settings dialog box even after "auto" and "apply" are set.    so can I do something else?

---

### Post by sailor2001 on 2008-09-14
in terminal (applications/accessories) gksudo displayconfig -gtk

---

### Post by bumanie on 2008-09-14
In terminal > sudo xfix if that doesn't work, reboot in recovery mode and choose "attempt to fix xserver" option.

---

### Post by adamogardner on 2008-09-14
booting into recovery and opting to fix xserver thing was ther way to go.

---

### Post by adamogardner on 2008-09-14
new problem:  my screen saver only covers a fraction (third) of the screen size.  Other than that the resolution is sharp, but my compiz settings aren't working.

---

