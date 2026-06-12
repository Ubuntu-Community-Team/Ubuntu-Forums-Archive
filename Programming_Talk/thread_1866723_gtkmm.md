---
title: "gtkmm"
date: 2011-10-21
forum: Programming Talk
---

### Post by sepoto on 2011-10-21
I used the Ubuntu Software Center and searched for gtkmm but I did not return any results. Is it installed by default on 11.1? If not is there a command line to install? What about prerequisite packages? Thanks!

---

### Post by cgroza on 2011-10-21
```

sudo apt-cache search gtkmm
[sudo] password for cgroza: 
gtkmm-documentation - Documentation of C++ wrappers for GLib/GTK+
libatkmm-1.6-dbg - C++ wrappers for ATK accessibility toolkit (debug symbols)
libgtkmm-2.4-1c2a - C++ wrappers for GTK+ (shared libraries)
libgtkmm-2.4-dbg - C++ wrappers for GTK+ (debug symbols)
libgtkmm-2.4-dev - C++ wrappers for GTK+ (development files)
libgtkmm-2.4-doc - C++ wrappers for GTK+ (documentation)
libgtkmm-3.0-1 - C++ wrappers for GTK+ (shared libraries)
libgtkmm-3.0-dbg - C++ wrappers for GTK+ (debug symbols)
libgtkmm-3.0-dev - C++ wrappers for GTK+ (development files)
libgtkmm-3.0-doc - C++ wrappers for GTK+ (documentation)

```You need the -dev package.

Did you click the "Show technical terms" ?

---

### Post by t1497f35 on 2011-10-22
As a **developer** you need to install libgtkmm-3.0-dev, the docs are in libgtkmm-3.0-doc (after installing the docs you can find the API at file:///usr/share/doc/libgtkmm-3.0-doc/reference/html/classes.html)

**Users** don't have to install anything to run a program written with gtkmm.

---

