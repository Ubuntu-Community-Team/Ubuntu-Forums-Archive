---
title: "gnome panel applet tutorial"
date: 2010-05-27
forum: Programming Talk
---

### Post by freeaks on 2010-05-27
hi there
i'm trying to follow this tutorial here:
[wedevblog.com/gnome-panel-applet-part-1]("http://www.wedevblog.com/gnome-panel-applet-part-1.html")
to learn making a gnome panel applet
i have installed build-essential package as well as libpanel-applet2-dev
but when i try to compile i get this error:
error: panel-applet.h: No such file or directory
error: gtk/gtklabel.h: No such file or directory
..
i can see /usr/include/panel-2.0/panel-applet.h
the file is here
but somehow i can't seem to be able to compile.. 
what could i do ?
i'm using this: g++ $(pkg-config –cflags –libs libpanelapplet-2.0) -o helloworld example-applet.c

tnx

---

### Post by freeaks on 2010-05-27
solved..
it's --cflags --libs and not &#8211;cflags &#8211;libs :)

---

