---
title: "C++ Libraries Configuration"
date: 2007-11-09
forum: Programming Talk
---

### Post by mkoehler on 2007-11-09
Good afternoon,

     I'm having some trouble when I install libraries from synaptic.  For example, I am trying to do some work with using GTK+ with Cairo, and in order to do so, I needed to download additional libraries (such as gtkmm-2.4).  However, in doing so, synaptic installed the library in the directory /usr/include/gtkmm-2.4.  This causes major problems when I try to compile, because the library's files cannot find the files it tries to include.  For example, here is a line in gtkmm-2.4/gtkmm/drawingarea.h:

```
#include <gtkmm/widget.h>
```

However, it works when I use the line:

```
#include <gtkmm-2.4/gtkmm/widget.h>
```

It is pretty obvious that g77 isn't looking in the subdirectories for the files; rather, it expects to find a /usr/include/gtkmm directory.  If anyone could tell me how to make g77 search specific subdirectories for files, it would be appreciated.

---

### Post by psusi on 2007-11-09
gcc -I/path/containing/include/files

Or just symlink the directory it wants to the one the files are actually in.

---

### Post by hod139 on 2007-11-09
Make sure you are downloading the -dev packages.

---

