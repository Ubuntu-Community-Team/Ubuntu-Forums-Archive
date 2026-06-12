---
title: "Trying To Install Cheese From SVN?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by kevin11951 on 2008-07-05
When i try to install cheese from the SVN repo, i get this error: 
```
Checking for required M4 macros...
  glib-gettext.m4 not found
  pkg.m4 not found
***Error***: some autoconf macros required to build cheese
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

help?

---

### Post by neurostu on 2008-07-05
Not sure how to solve this, you should probably talk to the developers of cheese.

btw, you know that cheese is in the repo's right?

---

### Post by kevin11951 on 2008-07-05
> **neurostu said:**
> Not sure how to solve this, you should probably talk to the developers of cheese.

btw, you know that cheese is in the repo's right?

yes, but the repos version is missing a feature i need (the ability to choose image resolution) and a bug (after a video is taken, the program freezes) both are fixed in the svn version

---

### Post by neurostu on 2008-07-05
try intalling:
```

libglib2.0-dev

```

---

### Post by kevin11951 on 2008-07-05
> **neurostu said:**
> try intalling:
```

libglib2.0-dev

```

already installed

---

### Post by neurostu on 2008-07-05
So you're getting that error when you run what?
autogen.sh?
configure?
make?

---

### Post by kevin11951 on 2008-07-05
> **neurostu said:**
> So you're getting that error when you run what?
autogen.sh?
configure?
make?

short answer autogen,
long answer:


```
ksoviero@ksoviero-laptop:~$ cd cheese
ksoviero@ksoviero-laptop:~/cheese$ ./autogen.sh
/usr/local/bin/gnome-autogen.sh
checking for autoconf >= 2.57...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.7...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9
checking for libtool >= 1.4.3...
  testing libtoolize... found 1.4.3
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.16.3
checking for intltool >= 0.40.0...
  testing intltoolize... found 0.40.0
checking for pkg-config >= 0.16.0...
  testing pkg-config... found 0.22
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.12.2
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.20.1
Checking for required M4 macros...
  glib-gettext.m4 not found
  pkg.m4 not found
***Error***: some autoconf macros required to build cheese
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

ksoviero@ksoviero-laptop:~/cheese$ 
```

---

### Post by neurostu on 2008-07-05
have you tried consulting the cheese website?  Have you tried on irc?

---

### Post by neurostu on 2008-07-05
From the README that comes with Cheese it says:
```

- glib-2.0 >= 2.15.5
8 		  - gio-2.0 >= 2.15.5
9 	63 	  - gobject-2.0
10 		  - gtk+-2.0 >= 2.10.0
11 		  - gdk-2.0
12 		  - dbus-1
13 	298 	  - hal
14 		  - cairo
15 	337 	  - pango
16 		  - librsvg >= 2.18.0
17 	298 	  - gstreamer-0.10 >= 0.10.15
18 		  - gstreamer-plugins-base-0.10  >= 0.10.15
19 	325 	  - gstreamer-plugins-good-0.10  >= 0.10.6
20 	163 	  - gstreamer-pango-0.10  >= 0.10.12
21 	63 	  - gnome-vfs-2.0
22 	148 	  - libgnomeui-2.0
23 	182 	  - xf86vidmodeproto
24 	150 	  - libebook-1.2 (evolution-data-server) 

```
are all required... (sorry about the numbers)
you might have to install the dev packages for each of them as well...

---

### Post by kevin11951 on 2008-07-05
> **neurostu said:**
> From the README that comes with Cheese it says:
```

- glib-2.0 >= 2.15.5
8 		  - gio-2.0 >= 2.15.5
9 	63 	  - gobject-2.0
10 		  - gtk+-2.0 >= 2.10.0
11 		  - gdk-2.0
12 		  - dbus-1
13 	298 	  - hal
14 		  - cairo
15 	337 	  - pango
16 		  - librsvg >= 2.18.0
17 	298 	  - gstreamer-0.10 >= 0.10.15
18 		  - gstreamer-plugins-base-0.10  >= 0.10.15
19 	325 	  - gstreamer-plugins-good-0.10  >= 0.10.6
20 	163 	  - gstreamer-pango-0.10  >= 0.10.12
21 	63 	  - gnome-vfs-2.0
22 	148 	  - libgnomeui-2.0
23 	182 	  - xf86vidmodeproto
24 	150 	  - libebook-1.2 (evolution-data-server) 

```
are all required... (sorry about the numbers)
you might have to install the dev packages for each of them as well...

ok, but i have all those... what would the packages be for those?

---

