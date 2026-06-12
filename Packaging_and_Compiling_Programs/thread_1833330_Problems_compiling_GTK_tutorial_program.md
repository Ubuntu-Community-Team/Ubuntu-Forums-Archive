---
title: "Problems compiling GTK tutorial program"
date: 2011-08-25
forum: Packaging and Compiling Programs
---

### Post by tripod87 on 2011-08-25
Hi all,

I'm trying to compile the GTK tutorial shown here - [http://developer.gnome.org/gtk-tutorial/2.90/c39.html](http://developer.gnome.org/gtk-tutorial/2.90/c39.html)

I know it's an older version, but it's what my machine has by default (Ubuntu 10.04).

I run
```
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
```

And I get this error:


```
Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gobject-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gobject-2.0', required by 'GdkPixbuf', not found
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function &#8216;main&#8217;:
base.c:6: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
base.c:6: error: (Each undeclared identifier is reported only once
base.c:6: error: for each function it appears in.)
base.c:6: error: &#8216;window&#8217; undeclared (first use in this function)
base.c:10: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)

```

I've installed nearly every package I can think of and can't find where gobject-2.0.pc would be.  I've run through most threads using search to look for what's wrong and have tried installing every package people have suggested and am seeing no success.  

Any help would be greatly appreciated!  Thanks!

---

### Post by Bachstelze on 2011-08-25
You need libgtk2.0-dev.

---

### Post by tripod87 on 2011-08-26
> **Bachstelze said:**
> You need libgtk2.0-dev.

I already have that installed, plus pretty much every other library anyone has suggested.

---

### Post by gmargo on 2011-08-27
From error message....

> 
```
Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `[COLOR=Red]gobject-2.0.pc[/COLOR]'
to the PKG_CONFIG_PATH environment variable


```Now go use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find out what package contains the file **gobject-2.0.pc** on Lucid:

[http://packages.ubuntu.com/search?searchon=contents&keywords=gobject-2.0.pc&mode=exactfilename&suite=lucid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gobject-2.0.pc&mode=exactfilename&suite=lucid&arch=any)

Here's the two possible files listed:
```

File                                          Packages        
/usr/lib/lsb3/pkgconfig/gobject-2.0.pc        [lsb-build-desktop3]("http://packages.ubuntu.com/lucid/lsb-build-desktop3")                       
/usr/lib/pkgconfig/gobject-2.0.pc             [libglib2.0-dev]("http://packages.ubuntu.com/lucid/libglib2.0-dev")

```But it's fairly obvious that only the second one applies: so you need to install the **libglib2.0-dev** package.

---

