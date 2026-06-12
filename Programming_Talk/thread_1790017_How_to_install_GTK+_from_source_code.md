---
title: "How to install GTK+ from source code"
date: 2011-06-24
forum: Programming Talk
---

### Post by morteza1991 on 2011-06-24
Hi
I downloaded GTK+ 3.0 from [http://www.gtk.org/download/linux.php](http://www.gtk.org/download/linux.php)
I'm trying to install it but can't
when I enter ./configure in terminal I see at the end
```
configure: error: Package requirements (glib-2.0 >= 2.28.0    atk >= 1.30    pango >= 1.24.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.22.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```can anyone help me?

---

### Post by Hairy_Palms on 2011-06-24
the easiest way to install gtk3 is either from ricotz gnome3 ppa or if you want to compile, by using jhbuild

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
[https://live.gnome.org/Jhbuild](https://live.gnome.org/Jhbuild)

---

### Post by cgroza on 2011-06-24
> **morteza1991 said:**
> Hi
I downloaded GTK+ 3.0 from [http://www.gtk.org/download/linux.php](http://www.gtk.org/download/linux.php)
I'm trying to install it but can't
when I enter ./configure in terminal I see at the end
```
configure: error: Package requirements (glib-2.0 >= 2.28.0    atk >= 1.30    pango >= 1.24.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.22.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```can anyone help me?
You have missing dependencies.

---

### Post by morteza1991 on 2011-06-25
I installed all dependencies 
```
glib, atk, pango, cairo, cairo-gobject, gdk-pixbuf
```
but when I configure I'm receiving the following error
```
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.28.0    atk >= 1.30    pango >= 1.24.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.22.0) were not met:

Requested 'cairo >= 1.10.0' but version of cairo is 1.8.8
No package 'cairo-gobject' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Hairy_Palms on 2011-06-25
your version of cairo is too old as it says, which is why if your set on compiling, your probably going to want to use jhbuild since it will compile dependancies too.

---

### Post by nvteighen on 2011-06-25
Why do you want to do this? If you're on Ubuntu 11.04 or Debian testing, install the libgtk-3-0 package and all dependency issues will be resolved automatically by APT. And if you plan to use GTK+ 3 for some project, install libgtk-3-dev.

APT exists for a reason, you know.

---

### Post by morteza1991 on 2011-06-29
> **Hairy_Palms said:**
> your version of cairo is too old as it says, which is why if your set on compiling, your probably going to want to use c since it will compile dependancies too.

I use KDE
Can I install jhbuild on KDE?

---

### Post by JupiterV2 on 2011-06-29
If you're determined to compile from source, install the '-dev' packages of your missing dependencies, otherwise you're just installing the runtime libraries. Example: libgtk2.0-dev

---

