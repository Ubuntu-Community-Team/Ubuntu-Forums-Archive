---
title: "Spawning windows in gtk--/glade-- apps"
date: 2007-02-15
forum: Programming Talk
---

### Post by sharperguy on 2007-02-15
Hi

I have recently begun trying to learn to write gtk+ applications with gtk-- and glade--.

After some messing around, I managed to get a simple test program to compile and run correctly.

I now want to add an about window popup to the program.

I created the window that is to pop up and the button that is meant to open it.

However I'm not sure how to get it to work.

I tried setting the visible property of the popup window to "no" and setting the handler for the button to gtk_widget_show and put in the name of the window, but it would not build the project.

I got an error saying that it could not determine the type of the popup window.

I'm guessing that the popup window is not accessible in that way from there.

So does anyone know how I would go about this properly?

---

