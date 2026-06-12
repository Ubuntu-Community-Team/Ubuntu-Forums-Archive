---
title: "webkit.h"
date: 2008-03-24
forum: Programming Talk
---

### Post by WarMonkey on 2008-03-24
I installed webkit with 
```
svn checkout http://svn.webkit.org/repository/webkit/trunk WebKit
```

So, why can't I compile programs containing 
```
#include <webkit/webkit.h>
```

with g++?

---

### Post by sq377 on 2008-03-24
the svn command you gave will only grab the latest webkit source code and put it in your working directory.  It doesn't install it for you.  There are a few development libraries in the apt repositories, i'd recommend using those.

libqtwebkit-dev - Web content engine library for Qt - Development files
libqtwebkit0d - Web content engine library for Qt
libqtwebkit1d - Web content engine library for Qt
libqtwebkit1d-dbg - Web content engine library for Qt - Debugging symbols
libwebkitgtk-dev - Web content engine library for Gtk+ - Development files
libwebkitgtk1d - Web content engine library for Gtk+
libwebkitgtk1d-dbg - Web content engine library for Gtk+ - Debugging symbols

---

### Post by Awalton on 2008-03-25
Post the whole string you used to attempt to compile your application.

Most likely the case is, you forgot to link to WebKit. 
(e.g. with WebKitGtk on Hardy: g++ file.cpp test `pkg-config --libs --cflags WebKitGtk`; pkg-config is just the easy way around having to remember where the libraries are and what flags you need to use, etc.)

---

