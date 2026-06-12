---
title: "Cannot find glib"
date: 2008-03-11
forum: Programming Talk
---

### Post by dgcampos on 2008-03-11
Hello people, if anyone can help with this, i appreciate it very much.

i try this command :

dgc@ubuntudgc:~/ProyectosGlade/proyecto1$ ./autogen.sh

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)
dgc@ubuntudgc:~/ProyectosGlade/proyecto1$ sudo apt-get install glib
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete glib

sorry is in spanish, but says "cannot find glib package"

how can i find this ? 

thank you very much to everyone.

dani

---

### Post by lnostdal on 2008-03-11
you already have glib installed actually .. but, since you are compiling something it is most likely looking for the development-files for glib

```

root@ibmr52:~# sudo aptitude search glib | grep dev
p   bglibs-dev                      - BG Libraries Collection                   
p   libavahi-glib-dev               - Development headers for the Avahi glib int
i   libdbus-glib-1-dev              - simple interprocess messaging system (GLib
p   libghc6-glib-dev                - A GUI library for Haskell (Gtk2Hs) -- GLib
v   libglib-dev                     -                                           
p   libglib-java-dev                - GLib bindings for Java (development files)
p   libglib1.2-dev                  - The GLib library of C routines (developmen
i   libglib2.0-dev                  - Development files for the GLib library    
i A libglibmm-2.4-dev               - C++ wrapper for the GLib toolkit (developm
p   libglrr-glib-dev                - Development library of Grift (glib)       
p   libmissinglib-ocaml-dev         - Library of utility functions for OCaml    
p   libnm-glib-dev                  - network management framework (GLib interfa
p   libpoppler-glib-dev             - PDF rendering library -- development files
p   libsofia-sip-ua-glib-dev        - Sofia-SIP library glib/gobject interface d
p   libtelepathy-glib-dev           - GLib Telepathy connection manager library 
p   libtelepathy-glib-unstable-dev  - GLib Telepathy connection manager library 
p   libxmmsclient++-glib-dev        - XMMS2 - glib client library for c++ - deve
p   libxmmsclient-glib-dev          - XMMS2 - glib client library - development 

root@ibmr52:~# sudo aptitude install libglib2.0-dev
...

```

---

### Post by geraldm on 2008-03-11
```

ls /usr/lib/{libglib-2.0.so.?,libgmodule-2.0.so.?,libgthread-2.0.so.?}

```

---

### Post by dgcampos on 2008-03-16
> **lnostdal said:**
> you already have glib installed actually .. but, since you are compiling something it is most likely looking for the development-files for glib


Thanks a lot!!!! i worked out, but now... another problem...

no look at this :

```

checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

i guess another sudo must be need..but which one????

thanks a lot man!!!!

---

### Post by lnostdal on 2008-03-17
every development library(#1) starts with the string "lib" and ends with "dev" .. so if some software is named "symbolicweb" it is likely that the development library for that software is named something like "libsymbolicweb-dev" or similar ... 

ok, so you are looking for some development library for gtk, so we try:

```

aptitude search libgtk.*dev

```

..which basically means "search for libgtk[something]dev"

the one you're after is:

```

i   libgtk2.0-dev                   - Development files for the GTK+ library    

```

..so..

```

sudo aptitude install libgtk2.0-dev

```


#1: at least the C based ones

---

