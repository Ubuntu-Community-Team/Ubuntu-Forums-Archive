---
title: "Problem installing mergeant-0.62 from source"
date: 2005-10-08
forum: Packaging and Compiling Programs
---

### Post by celle on 2005-10-08
Hi,
I tried to install mergeant-0.62 from source.  When run ./configure I got the message:
---
Package libgnomedb-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomedb-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomedb-2.0' found
configure: error: Package requirements (libgnomedb-2.0 >= 1.3.90         libgda-2.0 >= 1.3.90   gconf-2.0         gtk+-2.0 >= 2.4.0     gdk-pixbuf-2.0  libxml-2.0         libgnomeui-2.0 >= 2.0         libglade-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
Alternatively you may set the MERGEANT_CFLAGS and MERGEANT_LIBS environment variables
--
I have checked in directory "/usr/lib/pkgconfig" and I have only 'libgnomedb.pc'.  I just installed gnome-db and the
libgnomedb2-common & libgnomedb2-dev files, but this did not work ?  How is this libgnomedb-2.0.pc made ?

Any advice ?  Thanks

---

