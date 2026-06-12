---
title: "Can't find GTK+2 development files"
date: 2005-11-27
forum: Packaging and Compiling Programs
---

### Post by mjrmua on 2005-11-27
I'm trying to build wxWidgets 2.6 under breezy and am getting the following error when running configure:
```

checking for GTK - version >= 1.2.7... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking for gtk-config... (cached) no
checking for GTK - version >= 1.2.3... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
```

I've installed libgtk2.0-dev and libgtk+2.0-directfb-udeb-dev.  

Can't find gtk-config executable. 

pkg-config gtk+-2.0 --libs returns 
```

-lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0

```

but setting LD_LIBRARY_PATH to this has no effect.

any ideas?

---

### Post by uglysmurf on 2005-12-15
try the libgtk1.2-dev package

```
sudo apt-get install libgtk1.2-dev
```

---

### Post by bcarpenter on 2006-01-10
In case anybody has this problem, Uglysmurf's suggestion worked for me.

Thanks,
Brian

---

### Post by Tom_GayLUG on 2006-01-12
I had the same problem, for which 
```
sudo apt-get install libgtk1.2-dev
```
does not work on... however...
```
sudo apt-get install libgtk2.0-dev
```
does :)
:KS

---

### Post by slick666 on 2009-01-22
```
sudo apt-get install libgtk2.0-dev
```

Worked for me too

---

### Post by RainKap on 2009-11-11
I tried this - in fact I'd found by looking in Synaptic that libgtk2.0-dev was already installed. However I'm trying to build wxWidgets v2.4.2, which Audacity 1.2.6 requires; when I try the ./configure step with wxWidgets v2.4.2 it complains that it can't find gtk-config for gtk+ or gtk version >=1.2.7 or gtk version >=1.2.3 (as in the original post), so it looks as though I really need libgtk1.2-dev... Any idea where I can find it, please?

I've found from experience with Audacity v1.3.9 (the version which comes with Karmic) that I really need Audacity 1.2.6 to do a regular job processing the recordings of services at our church...

TIAFAH

Ian

---

### Post by RainKap on 2009-11-11
Sorry to be rather previous with my question; I found the files I needed starting at [http://packages.ubuntu.com/dapper/libgtk1.2-dev](http://packages.ubuntu.com/dapper/libgtk1.2-dev)

To satisfy all the dependencies, you need to download and install the following in the order shown:

libgtk1.2-common_1.2.10-18_all.deb
libglib1.2_1.2.10-10.1build1_amd64.deb
libgtk1.2_1.2.10-18_amd64.deb
libglib1.2-dev_1.2.10-10.1build1_amd64.deb
libgtk1.2-dev_1.2.10-18_amd64.deb

After that, I was able to build wxWidgets 2.4.2 OK.

Ian

---

### Post by rewolff on 2010-08-10
In Lucid libgtk1.2-dev no longer exists, and libgtk2.0-dev doesn't provide gtk-config .... Help!

---

