---
title: "What widget is the folder-button selector?"
date: 2009-12-30
forum: Programming Talk
---

### Post by NoBugs! on 2009-12-30
The nautilus file manager in Ubuntu has the handy file selector that will show buttons for each folder, for example if /home/username/folder/ is viewed, it will show 3 buttons, if the folders are too long to view, there are arrow-buttons to navigate left/right. Is there a special gtk widget to use this, or is it just a bunch of buttons in a special container??
I've looked through the catalog of gtk controls and I can't find this control...

---

### Post by kutya61 on 2010-01-21
You should check it in the source code. ;)

[http://ftp.gnome.org/pub/gnome/sources/nautilus/2.26/nautilus-2.26.3.tar.gz](http://ftp.gnome.org/pub/gnome/sources/nautilus/2.26/nautilus-2.26.3.tar.gz)

---

### Post by saulgoode on 2010-01-21
It is a [GtkPathBar]("http://git.gnome.org/browse/gtk+/tree/gtk/gtkpathbar.h"). I couldn't find it in the documentation.

---

