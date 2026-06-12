---
title: "Anjuta + Gnome programming"
date: 2008-09-25
forum: Programming Talk
---

### Post by prabath_fun on 2008-09-25
Hi,
  installed Anjuta and want to do some gnom programming.
  Just created project Generic gnome project. 
1. My build menu is disabled.
2. If I try "Run Configure" I AM getting 
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: error: Package requirements (libgnome-2.0 >= 2.14 libgnomeui-2.0 >= 2.14 libglade-2.0 >= 2.6.0    ) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_FOOBAR_CFLAGS
and GNOME_FOOBAR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Completed unsuccessful
Total time taken: 7 secs



as last few lines inmessage window.

I searched the packages 'libgnome-2.0', 'libgnomeui-2.0','libglade-2.0' in packages.ubuntu.com. But I am not getting it.
Please help me to solve.

---

### Post by jespdj on 2008-09-25
Maybe you need to install the GNOME development packages. Try installing the package **gnome-devel**.

---

