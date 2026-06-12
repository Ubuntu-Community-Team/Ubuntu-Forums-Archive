---
title: "Dealing with multiple versions of the same library"
date: 2009-05-05
forum: Programming Talk
---

### Post by kerryhall on 2009-05-05
Does anyone have a good document describing how to deal with having multiple versions of the same library? Let's say I have installed wxwidgets-dev package for some program I was working on. Now I need the bleeding edge wxwidgets source for some other program. Do I need to uninstall the old package before I build the new one? Should I be installing my build in /usr/local or /usr?

Thanks!

---

### Post by eye208 on 2009-05-05
In the case of wxWidgets it's quite easy because the version numbers are part of the library names, e.g.
```
libwx_gtk2u_core-2.8.so
```
So you will always use an option such as -lwx_gtk2u_core-2.8 when linking against wxWidgets 2.8.

In most cases however, the library version numbers are part of the library *file* name only, e.g.
```
libexif.so.12.2.0
```
When you install the libexif-dev package, a symbolic link
```
libexif.so -> libexif.so.12.2.0
```
will be added so that you can use the -lexif option to link against this library. In this case it's impossible to install several versions of the libexif-dev package side by side, because all of them contain the libexif.so symbolic link, targeting different versions of the library.

You can always build and install a local development version of a library by specifying an alternative installation prefix during configuration, e.g.
```
./configure --prefix=/home/me/local
```
or
```
cmake -DCMAKE_INSTALL_PREFIX=/home/me/local .
```
The easiest way to make GCC/G++, LD and PKG-CONFIG use this local version of the library is by setting some environment variables:
```
export CPATH=/home/me/local/include
export LIBRARY_PATH=/home/me/local/lib
export LD_LIBRARY_PATH=/home/me/local/lib
export PKG_CONFIG_PATH=/home/me/local/lib/pkgconfig
```

---

### Post by kerryhall on 2009-05-05
This is exactly what I needed to know. Thank you so much! :)

---

