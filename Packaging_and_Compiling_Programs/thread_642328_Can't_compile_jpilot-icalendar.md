---
title: "Can't compile jpilot-icalendar"
date: 2007-12-16
forum: Packaging and Compiling Programs
---

### Post by gjaffe on 2007-12-16
I'm trying to compile jpilot-icalendar-0.04, and I'm getting the following error from configure.

```
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: *** GTK >= 1.2.0 not installed - please install first ***
```

I tried installing libglib2.0-dev, but this didn't help.  I notice that there is also libglib1.2 and libglib1.2-dev available.  Do I have to install that too, and if I do, will that mess up my gtk2 installation?

Or is there something else I need to install?

Thanks for any help.

Gary

---

### Post by dholbach on 2007-12-18
GTK2 and GTK1 (and their glib equivalents) are installable in parallel. In this case you want to install libgtk2.0-dev.

---

### Post by dholbach on 2007-12-18
Hm, it could be libgtk1.2-dev too.

---

