---
title: "Strange error during make gobject-introspection"
date: 2012-05-30
forum: Packaging and Compiling Programs
---

### Post by ovidiugabriel on 2012-05-30
Hello,

I try to upgrade the glib on my system.
While compiling dependencies I found that make of gobject-instrospection halts with the following error:


/usr/local/include/glib-2.0/gio/gpollableoutputstream.h:88: Fatal: Gio: can't find parameter count referenced by parameter buffer of 'pollable_output_stream_write_nonblocking'
/usr/local/include/glib-2.0/gio/gpollableoutputstream.h:88: Fatal: Gio: can't find parameter count referenced by parameter buffer of 'pollable_output_stream_write_nonblocking'

I try to upgrade from glib-2.0 to glib-2.32.2 because version of cheese I need depends on gudev-1.0.

This error is very strange to me. I think I have to give the path to the new sources include directory to the build. The make is still using old include path. But make install of glib was successful. It is strange.
The same problem has been reported on Arch Linux.

Please help! Thanks!

---

### Post by oldos2er on 2012-05-31
Moved to Packaging and Compiling Programs.

---

### Post by ovidiugabriel on 2012-06-03
I also tried to get sources of cheese 2.21.5, and glib-2.10 is needed. I installed glib-2.10 successfully, but ./configure of cheese still detects glib-2.0:


checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.10.0   gtk+-2.0 >= 2.10.0   libgnomeui-2.0 >= 2.14.0   libglade-2.0 >= 2.6.0   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.15   gstreamer-plugins-base-0.10 >= 0.10.15   gnome-vfs-2.0 >= 2.18.0   libebook-1.2 >= 1.12.0   cairo >= 1.2.4   dbus-1 >= 1.0   hal >= 0.5.9   dbus-glib-1 >= 0.7   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0   xxf86vm) were not met:

Does anyone knows how to change the path to the new glib?

---

### Post by johncc330 on 2012-06-28
> but ./configure of cheese still detects glib-2.0:

Probably already solved, but still:

The generic 'familty' of glib is called 2.0, configure is testing against 2.10, but the line you included doesn't show which test failed. That normally appears in the next lines after the one you posted. (after the 'were not met:')

John

---

