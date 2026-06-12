---
title: "Ubuntu natty building gtk+-3.2.3"
date: 2012-01-03
forum: Packaging and Compiling Programs
---

### Post by nocturnal1 on 2012-01-03
I'm trying to build gtk+-3.2.3 on Ubuntu natty. This is a fresh Ubuntu install with security updates only. I have not installed gtk3 prior to this.
First I installed:
```
sudo apt-get install libffi-dev zlib1g-dev fam libdbus-1-dev libdbus-glib-1-dev gobject-introspection libxext-dev libxrender1-dbg colordiff libcairo2-dev libtiff4-dev libpng12-dev libxft-dev libxi-devel
```I have the following folders in the directory /home/nocturnal1/gtk

atk-2.1.5
gdk-pixbuf-2.24.1
glib-2.30.1
gtk+-3.2.3
pango-1.29.1

Then I do the following from the command line:
```

cd /home/nocturnal1/gtk/glib-2.30.1
./configure && make 
rm -rf /home/nocturnal1/gtk/include/glib.h  /home/nocturnal1/gtk/include/gmodule.h  (glib INSTALL instructions) 
make install
```repeat for the other folders except without the rm, in the following order:

1. atk-2.1.5
2. gdk-pixbuf-2.24.1
3. pango-1.29.1
4. gtk+-3.2.3

Before running ./configure for gtk+-3.2.3 I enter this on the command line:

```

CPPFLAGS="-I/home/nocturnal1/gtk/include" 
LDFLAGS="-L/home/nocturnal1/gtk/lib" 
PKG_CONFIG_PATH="/home/nocturnal1/gtk/lib/pkgconfig" 
export CPPFLAGS LDFLAGS PKG_CONFIG_PATH 
LD_LIBRARY_PATH="/home/nocturnal1/gtk/lib" 
PATH="/home/nocturnal1/gtk/bin:$PATH" 
export LD_LIBRARY_PATH PATH 
export PKG_CONFIG_PATH="/home/nocturnal1/gtk/lib/pkgconfig:$PKG_CONFIG_PATH"
```I get the these errors when I run make on gtk+-3.2.3:


```

gdkwindow-x11.c: In function '_gdk_x11_moveresize_handle_event':
gdkwindow-x11.c:4301:9: error: 'XIEvent' undeclared (first use in this function)
gdkwindow-x11.c:4301:9: note: each undeclared identifier is reported only once for each function it appears in gdkwindow-x11.c:4301:18: error: 'ev' undeclared (first use in this function)
gdkwindow-x11.c:4301:33: error: expected expression before ')' token
gdkwindow-x11.c:4302:9: error: 'XIDeviceEvent' undeclared (first use in this function)
gdkwindow-x11.c:4302:24: error: 'xev' undeclared (first use in this function)
gdkwindow-x11.c:4302:46: error: expected expression before ')' token
gdkwindow-x11.c:4306:16: error: 'XI_Motion' undeclared (first use in this function)
gdkwindow-x11.c:4308:13: warning: implicit declaration of function '_gdk_x11_device_xi2_translate_state'
gdkwindow-x11.c:4313:16: error: 'XI_ButtonRelease' undeclared (first use in this function)
make[4]: *** [gdkwindow-x11.lo] Error 1
make[4]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk/x11'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3'
make: *** [all] Error 2
```Can anyone **Please help** :(

---

### Post by azmyth on 2012-01-05
Your package didn't get installed properly since you had the wrong name. It's libxi-dev not libxi-devel. This contains the function you're missing.

---

### Post by nocturnal1 on 2012-01-16
Thanks I see the misspelling. I had other issues unrelated so I did a complete reinstall. 

[LIST=1]
[*]Removed Ubuntu using Wubi.
[*]Full disk reformat from Windows. (Ubuntu sits on a external USB HDD)
[*]Reinstalled Ubuntu using Wubi.
[*]Ran Ubuntu security updates only.
[*]```
sudo apt-get install libffi-dev zlib1g-dev fam libdbus-1-dev  libdbus-glib-1-dev gobject-introspection libxext-dev libxrender1-dbg  colordiff libcairo2-dev libtiff4-dev libpng12-dev libxft-dev  libxi-dev
```
[*]Repeat as before.
[/LIST]
There are no fatal errors but I did notice these errors during make for gtk+-3.2.3
```
make[4]: Entering directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk/tests'
  CC     gdk-color.o
  CCLD   gdk-color
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_dup_objv'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_take_ref'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_new_objv'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_unix_open_pipe'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_unix_set_fd_nonblocking'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_cclosure_marshal_generic'
collect2: ld returned 1 exit status
make[4]: *** [gdk-color] Error 1
make[4]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk/tests'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3'
make: *** [all] Error 2
```And these errors during make install:
```

make[3]: Entering directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk/tests'
  CCLD   gdk-color
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_dup_objv'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_take_ref'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_variant_new_objv'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_unix_open_pipe'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_unix_set_fd_nonblocking'
/home/nocturnal1/gtk/lib/libgio-2.0.so: undefined reference to `g_cclosure_marshal_generic'
collect2: ld returned 1 exit status
make[3]: *** [gdk-color] Error 1
make[3]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk/tests'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/nocturnal1/gtk/gtk+-3.2.3/gdk'
make: *** [install-recursive] Error 1
```Also I'm not able to compile an application. I get these messages: 
```
Package gtk+-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-3.0' found
cssbutton2.c:6:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
```

---

### Post by azmyth on 2012-01-24
Google and apt-file are your friend when you try to compile.

```
sudo apt-get install apt-file
apt-file update
```

The functions are in header files that you're missing so take one of your functions and search on google

and you'll see it's in glib.h

[http://www.manpagez.com/html/glib/glib-2.30.0/glib-GVariant.php](http://www.manpagez.com/html/glib/glib-2.30.0/glib-GVariant.php)

then

apt-file search glib.h

and install the proper dep

you'll have to do this for any errors. Eventually you will square them away.

---

