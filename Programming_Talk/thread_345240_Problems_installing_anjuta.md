---
title: "Problems installing anjuta"
date: 2007-01-24
forum: Programming Talk
---

### Post by EricDallal on 2007-01-24
I was hoping to try Anjuta, but I have run into problems with the installation. The error message upon doing ./configure was as follows:

checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.8.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Can anybody tell me what the problem is? I can't imagine that glib would not be there if I have applications (ex: synaptic package manager that were written with GTK+).

Thanks in advance.

Eric.

---

### Post by EricDallal on 2007-01-24
I looked this problem up and found another post describing the same problem. It helped, but I still have problems. Essentially, I kept getting missing package errors, then installing the package and trying again. But now I am stuck because it seems that a newer version of the package is required than the one in the synaptic package manager:

checking for GDL... configure: error: Package requirements (gdl-1.0 >= 0.7.0 gdl-gnome-1.0 >= 0.7.0) were not met:

Requested 'gdl-1.0 >= 0.7.0' but version of gdl is 0.6.1
No package 'gdl-gnome-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDL_CFLAGS
and GDL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Does anybody know how to get a newer version?

---

### Post by hampycalc on 2007-01-30
Yeah, I have the same problem as stated above.
If anyone has any ideas, I'd be grateful too!
Tom

---

### Post by Tomosaur on 2007-01-30
If you're compiling anjuta from source, you will need the glib dev package:
```

sudo aptitude install libglib2.0-dev

```

I seem to remember that's what I did to get anjuta working, as I also had the same error initially. If you're getting package missing errors, download the dev package of the package in question and see if that works.

---

### Post by talowe on 2007-01-30
> **EricDallal said:**
> 

Requested 'gdl-1.0 >= 0.7.0' but version of gdl is 0.6.1
No package 'gdl-gnome-1.0' found

...

Does anybody know how to get a newer version?

you can get the tarball from [http://ftp.gnome.org](http://ftp.gnome.org) or the latest development version from svn.gnome.org

I don't remember for sure, but you might need a newer version of gnome-build (libgbf?) than is available from the repos.  (available fro the same places).  glade3 also (for glade integration, but that might be in repos now?)

---

### Post by theDentist on 2007-01-31
I had problems too, I always seemed to have libraries that were not the correct version so I decided to try anjuta version 1.2.4a, and older version, I installed it with no problems.  I know it's not the latest version but it didn't seem to matter, it did everything I wanted it to do.

Peter

---

### Post by theDentist on 2007-01-31
Just another note, Everything I needed, I was able to install from synaptic

Peter

---

### Post by Oskr on 2007-02-10
You can download the gdl latest version from here [gdl 0.7.0]("http://ftp.gnome.org/pub/GNOME/sources/gdl/0.7/"), the link is in the Anjuta 's download page. 

Then you will be ask for the gnome-build-0.1.0 package that can be downloaded [here]("http://ftp.gnome.org/pub/GNOME/sources/gnome-build/0.1/") .

But when i try to install that package i get:

 *** No hay ninguna regla para construir el objetivo `libgbfmarshal.list', necesario para `libgbfmarshal.h'.  Alto.

*** There is no rule to build the target `libgbfmarshal.list', needed for `libgbfmarshal.h'.  Stop.

Please post if you know something about this.

:lolflag:

---

### Post by sal_m on 2007-02-21
Oskar,

You need to install the libgbf-1-dev files.  At least, that worked for me.

---

### Post by Sabot on 2007-04-26
You need to install libglib2.0-dev to get anjuta to recognise your glib.

---

### Post by koala114 on 2007-07-22
Hi, you could download this package that contain libgbfmarshal.list from [http://debian.mirror.inra.fr/debian/pool/main/g/gnome-build/gnome-build_0.1.7.orig.tar.gz](http://debian.mirror.inra.fr/debian/pool/main/g/gnome-build/gnome-build_0.1.7.orig.tar.gz)
And I make it

---

