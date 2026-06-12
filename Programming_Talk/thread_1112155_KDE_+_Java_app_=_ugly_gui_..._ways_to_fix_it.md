---
title: "KDE + Java app = ugly gui ... ways to fix it?"
date: 2009-03-31
forum: Programming Talk
---

### Post by skullmunky on 2009-03-31
Hi, 

I'm using a Java app in KDE4, and the GUI isn't rendering so good.  Widgets seem to be missing, or are showing only the text, etc ... the scrollbar is missing, the menus (which have a lot of submenus), are missing the borders, and so on.  

The app specifically is the Arduino IDE ([www.arduino.cc](www.arduino.cc)), for programming Arduino AVR microcontroller boards.  Processing ([www.processing.org](www.processing.org)) has the same issue for me.  

I get a lot of these errors, too:
```

QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPainter::begin: Cannot paint on a null pixmap
QPainter::save: Painter not active
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::restore: Unbalanced save/restore
QPainter::end: Painter not active, aborted

(<unknown>:8229): Gdk-CRITICAL **: gdk_pixmap_foreign_new_for_display: assertion `(anid != 0)' failed

(<unknown>:8229): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(<unknown>:8229): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by amrypma on 2009-06-04
You don't have to use their IDE. if you get the arduino sources and the right mix of packages you can write adruino app's in any editor you like.
If I have the time I'd dig it out of the arduino.cc forums, but, right now I don't.

--Edit

But I do!

[http://www.arduino.cc/playground/Main/DevelopmentTools](http://www.arduino.cc/playground/Main/DevelopmentTools)

---

