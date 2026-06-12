---
title: "Gtk C++ Headers"
date: 2011-06-04
forum: Programming Talk
---

### Post by scott-ian on 2011-06-04
What package contains the C++ headers for Gtk?

---

### Post by simeon87 on 2011-06-04
libgtkmm-2.4-dev.

---

### Post by scott-ian on 2011-06-04
I have libgtkmm-2.4-dev installed, but I still get this error:
**main.cxx:24:21: fatal error: gtk/gtk.h: No such file or directory**

---

### Post by ThatCoolGuy220 on 2011-06-04
you should copy them into the include folder...

well at least worked for me for the "Cygwin" one

Also are you using an IDE?

---

### Post by scott-ian on 2011-06-04
Problem solved.  I built with this command:
g++ `pkg-config --cflags --libs gtk+-2.0` -Wall -c "%f"

---

### Post by simeon87 on 2011-06-04
Did you add it to gcc's arguments? See [this thread](http://ubuntuforums.org/showthread.php?t=637895).

---

