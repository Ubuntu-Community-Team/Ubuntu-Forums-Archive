---
title: "help in gtk+ programming"
date: 2008-06-04
forum: Programming Talk
---

### Post by montamer on 2008-06-04
hi 
how can i capture mouse click event in gtk+ programming
what i require is that the application to capture the mouse click signal when clicked anywhere on the application irrespective of the widgets on the main window and do something
how can i do this?
im new to this GUI programming

---

### Post by MicahCarrick on 2008-06-04
This is a very fundamental part of GUI programming. You may want to read through the Hello World GTK+ tutorial and possible [GTK+ and Glade3 GUI Programming Tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html").

You should understand how "widgets" are objects which inherit properties (and signals) from their parents.

You should understand how the GTK+ main loop waits for an event and emits "signals" for event which you connect callback functions to.

So, to answer your question, if you want to handle mouse clicks on the entire application, you do so using the "button-press-event" signal of the GtkWindow. In the your signal handler, you can check for which button was pressed and run code accordingly.

---

