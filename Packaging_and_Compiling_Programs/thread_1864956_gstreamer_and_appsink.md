---
title: "gstreamer and appsink"
date: 2011-10-19
forum: Packaging and Compiling Programs
---

### Post by wb4zuy@amsat.org on 2011-10-19
Has anyone else tried linking a gstreamer application that uses any appsink calls.  They all seem to be unresolved.  A quick search shows no libgstappsink.so anywhere.  Ubuntu 11.04, gstreamer 0.10.30.  I'm wondering if we got caught between the time that appsink moved from the bad plugins and showed up in the base plugins.  Any help appreciated.

Wynn Rostek

---

### Post by SevenMachines on 2011-10-20
I havent used gstreamer but is it not?
```
 -lgstapp-0.10
```or better
```
 gcc -o example example.c `pkg-config --cflags --libs gstreamer-app-0.10`
```where 
```
$ pkg-config --cflags --libs gstreamer-app-0.10
-pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/gstreamer-0.10 -I/usr/include/libxml2  -pthread -lgstapp-0.10 -lgstbase-0.10 -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lxml2 -lgthread-2.0 -lrt -lglib-2.0
```If you have example code of compilation failing to look at?

---

