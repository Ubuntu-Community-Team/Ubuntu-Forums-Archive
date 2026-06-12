---
title: "could not run GTK+ test program"
date: 2007-03-15
forum: Programming Talk
---

### Post by xrin on 2007-03-15
Hi,

I am trying to install wxPython when i met the following error.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the 
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please ensure that
pkg-config is in the path and that gtk+-2.0.pc is installed. For GTK+ 1.2 please
check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config --libs' are in the LD_LIBRARY_PATH or
equivalent.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

when i try to install libgtk2.0-dev it request for libpango1.0-dev.
when i try to install libpango1.0-dev it request for libx11-dev.
when i try to install libx11-dev, it request for libxext-dev.
But when installing libxext-dev, it request for libx11-dev again????

anyone can help on the above....................

thanks in advance....

---

### Post by fct on 2007-03-15
apt-get install gnome-core-devel

---

### Post by poleman on 2007-03-22
> **fct said:**
> apt-get install gnome-core-devel

It also happens in my computer when trying to compile wxwidgets. The above didn't solve the problem.

---

### Post by rogerdpack on 2009-05-13
> **fct said:**
> apt-get install gnome-core-devel

apt-get install libgtk2.0-dev 

might help

---

### Post by gouboft on 2011-11-19
I have got this
check the config.log,the libffi.so is missing

configure:29767: checking for GTK+ - version >= 2.4.0
configure:29887: gcc -o conftest  -pthread -I/usr/local/include/gio-unix-2.0/ -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     conftest.c -pthread -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0    -lm >&5
/usr/bin/ld: [COLOR="red"]warning: libffi.so.5, needed by /usr/local/lib/libgio-2.0.so, not found [/COLOR](try using -rpath or -rpath-link)
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_pointer'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_float'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_void'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_sint64'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_prep_cif'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_uint32'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_double'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_call'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_sint32'
/usr/local/lib/libgobject-2.0.so: undefined reference to `ffi_type_uint64'
collect2: [COLOR="Red"]ld returned 1 exit status[/COLOR]



So, find out the libffi.so and link to /usr/local/lib/
Note: make sure the libfi.so.6.0.0 is under the /usr/lib/i386-linux-gnu/
$ cd /usr/local/lib
$ sudo ln -s  ../../lib/i386-linux-gnu/libffi.so.6.0.0 libffi.so.5
$ sudo ln -s  ../../lib/i386-linux-gnu/libffi.so.6.0.0 libffi.so
:)

---

