---
title: "c++ and GUI"
date: 2008-03-27
forum: Programming Talk
---

### Post by StOoZ on 2008-03-27
except from QT, are there any GUI libaries in linux which I can use to write programs that will also run in windows? (using C++)

---

### Post by LaRoza on 2008-03-27
I would suggest wxWidgets, as it look native on all platform (that it is available)

You can also use GTK.

See my wiki, under "GUI"

---

### Post by WW on 2008-03-27
According to their web pages, these can: [gtkmm](http://www.gtkmm.org/) (the C++ binding of GTK+), [FLTK](http://www.fltk.org/), [wxWidgets](http://www.wxwidgets.org/).  (The only one that I've tried in a cross-platfrom app. is FLTK.)

---

### Post by StOoZ on 2008-03-27
im a GUI newbie ,never did any GUI before with c++, up to now I thought that GUI (a cross platform one that will run also on windows) can only be done with QT

---

### Post by kknd on 2008-03-27
> **WW said:**
> According to their web pages, these can: [gtkmm](http://www.gtkmm.org/) (the C++ binding of GTK+), [FLTK](http://www.fltk.org/), [wxWidgets](http://www.wxwidgets.org/).  (The only one that I've tried in a cross-platfrom app. is FLTK.)

+1.

For "portability", wxWidgets do the best job. But the others are also portable (gtkmm gives more work, but it's my choice for C++ gui).

FLTK is more limited than the others, but is also smaller and faster.

---

### Post by StOoZ on 2008-03-27
wxWidgets seems cool, thanks.
also , is there a reason why QT is less popular (I guess, just have the feeling ..)?

---

### Post by LaRoza on 2008-03-27
> **StOoZ said:**
> wxWidgets seems cool, thanks.
also , is there a reason why QT is less popular (I guess, just have the feeling ..)?

QT is popular. Many apps use it (on Linux and Windows).

KDE is built with QT (and most KDE apps use it), and GNOME uses GTK+. Ubuntu uses GNOME, so it may seem like QT is sparse.

QT can be used on KDE and GNOME, so you don't have to worry about that.

---

### Post by StOoZ on 2008-03-27
the only irritating thing I found (up to now..) in qt,is the amount of irrelevant stuff it install when you want to install it on windows...
70 FREAKIN MB's?!
why cant they just let me to install the libraries, which im sure just few mb's.

its sad that,where I learn,there is a slow internet, no optical drives, so how can I download 70MB + minigw .. :(
the only setback I found on QT... 
I dont need the designer etc.... What I looked for is just something to install, the minimalist as possible that will let me run qt app's on windows.

---

### Post by stevescripts on 2008-03-27
FWIW - Tk is also cross-platform, and it actually looks better (with defaults) on windows
than linux.  (meaning tk looks better on windows than Tk looks on linux)

Others mentioned may give the user more of a look and feel they desire

Steve

---

