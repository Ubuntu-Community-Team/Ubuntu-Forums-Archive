---
title: "How to install GTK+"
date: 2011-01-23
forum: Programming Talk
---

### Post by romy.mathew on 2011-01-23
HI 

I was planning to install GTK+ on my ubuntu...I tried to run the command which I found in the ubuntu[/COLOR] form 
"sudo aptitude install gnome-core-devel build-essential"

But i am getting error like
[COLOR="Red"]
"
romy@romy-laptop:~/temp/GTK_prog$ g++ base.c -o base 'pkg-config --cflags --libs gtk+-2.0'
g++: pkg-config --cflags --libs gtk+-2.0: No such file or directory
base.c:3:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘int main(int, char**)’:
base.c:8: error: ‘GtkWidget’ was not declared in this scope
base.c:8: error: ‘window’ was not declared in this scope
base.c:10: error: ‘gtk_init’ was not declared in this scope
base.c:12: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
base.c:12: error: ‘gtk_window_new’ was not declared in this scope
base.c:13: error: ‘gtk_widget_show’ was not declared in this scope
base.c:15: error: ‘gtk_main’ was not declared in this scope
"[/COLOR]

I then opened the Installation manual from [http://library.gnome.org/devel/gtk/stable/gtk-building.html](http://library.gnome.org/devel/gtk/stable/gtk-building.html)
for compiling and started a fresh download of GTK+2.22.tar.gz

1. I untar the file in download section GTK+-2.22.1
2. From the instruction from the manual i run ./configure --
   prefix=/opt/gtk 

Now there showed some base dependency error as below

[COLOR="red"]"
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.25.10    atk >= 1.29.2    pango >= 1.20    cairo >= 1.6    gdk-pixbuf-2.0 >= 2.21.0) were not met:

Requested 'glib-2.0 >= 2.25.10' but version of GLib is 2.24.1
Requested 'gdk-pixbuf-2.0 >= 2.21.0' but version of GdkPixbuf is 2.20.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"[/COLOR]

4. From [http://www.gtk.org/download-linux.html](http://www.gtk.org/download-linux.html), I downloaded 
   Glib2.26
5. Then run the command ./configure --prefix=/opt/gtk

But still the problem exist please somebody guide me to compile the demo program of base.c from 
[http://www.gtk.org/tutorial1.2/gtk_tut-2.html](http://www.gtk.org/tutorial1.2/gtk_tut-2.html)

Many Thanks

---

### Post by gmargo on 2011-01-23
Make sure you have the **libgtk2.0-dev** package installed.

> 
[COLOR=Red][COLOR=Black]romy@romy-laptop:~/temp/GTK_prog$ g++ base.c -o base 'pkg-config --cflags --libs gtk+-2.0'[/COLOR]
[COLOR=Black]g++: pkg-config --cflags --libs gtk+-2.0[/COLOR]: No such file or directory
[/COLOR][COLOR=Red]
[COLOR=Black]The quotes on your compile line - they should be backticks instead.  The compile line should look like:
```

gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`

```Also, you might prefer to follow the 2.0 tutorial: [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)
[/COLOR] [/COLOR]

---

### Post by lab_dragon on 2011-09-04
> **romy.mathew said:**
> 

[COLOR=red] checking for BASE_DEPENDENCIES... nogt
configure: error: Package requirements (glib-2.0 >= 2.25.10    atk >= 1.29.2    pango >= 1.20    cairo >= 1.6    gdk-pixbuf-2.0 >= 2.21.0) were not met:

Requested 'glib-2.0 >= 2.25.10' but version of GLib is 2.24.1
Requested 'gdk-pixbuf-2.0 >= 2.21.0' but version of GdkPixbuf is 2.20.1
"[/COLOR]


You are probably not using recent ubuntu (11.04 or 10.10). You should use older version of gtk+. I use 2.10.0 with my 10.4 lucid (kernel v. 2.6.32-28 ). 
However during cofigure i got error: 
```
configure: error:
*** Checks for JPEG2000 loader failed. You can build without it by passing
*** --without-libjasper to configure
```for** libjasper, libtiff **and** libjpg**

after running: 
```
$sudo su
#apt-get install libjasper-dev
#apt-get install libjasper1
#apt-get install libtiff-opengl
#apt-get install libtiff4-dev
#apt-get install libjpg-opengl

```configure succeeded

---

### Post by Bachstelze on 2011-09-04
This thread is over six months old, please don't revive old thread.

---

