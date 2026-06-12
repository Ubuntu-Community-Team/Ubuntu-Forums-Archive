---
title: "Reserving X server Screen Space with Java for Swing windows"
date: 2009-03-19
forum: Programming Talk
---

### Post by C-- on 2009-03-19
Hello. I am attempting to construct a Java application that needs to reserve screen space at the top of the screen in an X server. Reserving this space will prevent other windows from being dragged behind it. It is not enough to merely state that the windows are always on top because windows can still be dragged behind it; the space must be reserved. This is similar to the behavior of the gnome and kde panels, although my application doesn't need to have the ability to move around: it will stay fixed at the top of the screen.

I already know that you can reserve space using C, GTK+, and Xlib calls. I have already tried using the XChangeProperty function to change the _NET_WM_STRUT_PARTIAL property of a GtkWindow; defining a window's struts allows it to reserve space along the edge of the screen.

However I need to be able to do this with Java and Swing. I do not know of any Xlib Java bindings, and as far as I know Xlib functions only take GTK windows as arguments, not Swing components.

Does anyone know of a way to reserve screen space or define struts for Swing GUIs in Java such that screen space is reserved along the top of an Xserver screen?

---

### Post by Reiger on 2009-03-19
This might be a good place to start: [https://jna.dev.java.net/](https://jna.dev.java.net/)

---

