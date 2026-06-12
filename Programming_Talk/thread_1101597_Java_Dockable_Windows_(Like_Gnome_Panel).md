---
title: "Java Dockable Windows (Like Gnome Panel)"
date: 2009-03-20
forum: Programming Talk
---

### Post by C-- on 2009-03-20
I am developing a Java Swing application that will run in Gnome in an X11 environment with the Metacity window manager. My application will consist of one window that needs to be permanently displayed at the top of the screen, does not allow other windows to move under it, is always on top, and does not appear in the window list applet at the bottom of the screen.

I know how to do this in C and GTK+; just use XChangeProperty to set the window's _NET_WM_STRUT and _NET_WM_STRUT_PARTIAL atoms to reserve screen space and set the window type hint to GDK_WINDOW_TYPE_HINT_DOCK to remove decorations, window list entry, and the ability to drag.

However I cannot seem to do this in Java/Swing. Because of certain constraints I need to use this language/toolkit, and X calls only take Gdk windows as far as I know. Furthermore I do not know of any Java Xlib bindings.

Does anyone know how to make a Java dock/panel with reserved space?

---

### Post by doorman on 2009-03-20
you can use gtk in java as well, but you need to keep in mind the bindings are not cross platform.

You should look into the [java-gnome project]("http://java-gnome.sourceforge.net/")

---

### Post by C-- on 2009-03-22
Thank you for the suggestion. I had looked into Java-gnome, but unfortunately I have to use Swing for this particular project.

---

