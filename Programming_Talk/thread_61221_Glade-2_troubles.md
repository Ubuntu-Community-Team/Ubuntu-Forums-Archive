---
title: "Glade-2 troubles"
date: 2005-08-30
forum: Programming Talk
---

### Post by spacemonkey on 2005-08-30
I recently installed Glade-2, and it will not generate the C++ code for me.

Here is the error message I get:

```
Error running glade-- to generate the C++ source code.
Check that you have glade-- installed and that it is in your PATH.
Then try running 'glade-- <project_file.glade>' in a terminal.
``` 

I can find the file glade-2, but I can't find glade--.  According to synaptic, glade-- wasn't installed with the package.  Any ideas?

---

### Post by Shen on 2005-09-01
Glade can compile C by itself, but it needs either *gtkmm* or *glade--* to compile C++, neither of which is installed along with glade-2.

[http://home.wtal.de/petig/Gtk/](http://home.wtal.de/petig/Gtk/) is where you need to go.

---

### Post by spacemonkey on 2005-09-01
excellent, thanks for the help!

---

