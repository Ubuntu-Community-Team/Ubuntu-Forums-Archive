---
title: "PyGTK question (Hide VBox Overflow)"
date: 2009-04-20
forum: Programming Talk
---

### Post by sekinto on 2009-04-20
If I have a VBox how do I make it so that if its children try to exceed it's boundaries instead of forcing it's children to shrink it just cuts off anything going out of its boundaries (something similar to CSS's overflow:hidden; )?

(See attachment for visual example of what I'm trying to achieve.)

---

### Post by sekinto on 2009-04-21
Bump

---

### Post by cabalas on 2009-04-21
I don't think what you want to do is possible with Gtk, However the way I would do it is to wrap the VBox in a [ScrolledWindow]("http://www.pygtk.org/pygtk2reference/class-gtkscrolledwindow.html").

That should do something similar to what you want.

---

### Post by sekinto on 2009-04-21
But I don't want scrollbars or even the ability to scroll to be present. Although if there really is no other way I guess I will have to resort to that.

---

### Post by cabalas on 2009-04-21
If you don't want that then I'd suggest that you keep track of the number of children in the vbox if there are more than X you set any the visibility of any new children to be false.  When you remove a child you'll have to go through the children and choose one to have it's visibility turned on.

---

### Post by sekinto on 2009-04-23
When I try adding a scrolled window around the vbox I get an error saying vbox is not a scrollable widget, and to use a viewport with the scrolled window. When I surround my vbox with a viewport and the viewport with the scrolled window I cannot see the vbox when I start my app.

---

### Post by sekinto on 2009-04-24
Bump.

---

### Post by Kilon on 2009-04-25
> **sekinto said:**
> If I have a VBox how do I make it so that if its children try to exceed it's boundaries instead of forcing it's children to shrink it just cuts off anything going out of its boundaries (something similar to CSS's overflow:hidden; )?

(See attachment for visual example of what I'm trying to achieve.)

Without having any knowledge about PyGTK ( I am using WxPython) I would assume that this would required some "hacking" probably you would like to make your own classes that override the exist one and change the behaviour. 

Probably override the functions responsible for the shrink and replace them with your own. This way you will be able to change the behavior without changing the libraries and messing with PyGTK or GTK+. One of the big advantages of OOP. 

you should be looking for tutorials to customise the PyGTK and GTK+ by class inheritance. 

something along these lines 

[http://www.pygtk.org/articles/writing-a-custom-widget-using-pygtk/writing-a-custom-widget-using-pygtk.htm](http://www.pygtk.org/articles/writing-a-custom-widget-using-pygtk/writing-a-custom-widget-using-pygtk.htm)

---

### Post by Vadi on 2009-04-25
Just hide the widgets you'd like not to be shown.

---

