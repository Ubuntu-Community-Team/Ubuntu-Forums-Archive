---
title: "Creating a custom widget in Glade"
date: 2009-06-13
forum: Programming Talk
---

### Post by Tony Flury on 2009-06-13
I would like to be able to use glade to create a custom widget (using Glade 3.4).

I can write a python class for the new widget, which will do everything I need - it will Sub-class widget, trap a number of signals from the child elements, and generate its own signals a neccessary, and also define some new methods to allow the application to use the widget as a single entity.

What i don't know how to do is the following :

1) How do I use glade to create the GUI component of my widget

2) How do I add my custom widget to the glad palette, so I can include it in my application

3) when I open the glade file in my application, do I need to inform the gtk.glade library where the module is that defines the behaviour of my custom widget, and if not, how does GTK know how this widget will behave ?

I do have an alternative method to create & use my custom widget, by I would prefer to use Glade if i can.

---

### Post by Tony Flury on 2009-06-15
A very gentle bump - if someone can help. I am assuming it is possible.

---

### Post by Tony Flury on 2009-06-17
Since I have had no replies I am going to guess that Glade cannot natively support the construction of the GUI elements of a custom widget.

What I propose to do is as follows : 
Design my application GUI - and place frames suitably named where i actually want my widget.

I can then construct a class which extends GTK_Widget and uses the GTK library to construct the GUI elements, and I can then use the libglade within my application to find the frames, and place the widget inside those frames.

Does anyone see any reason why this wont work ?

---

### Post by tom.k.cook on 2012-06-06
I've just killed a day or so trying to figure this out, with no luck.  Using custom Gtk-- widgets in a Glade catalog doesn't seem to be supported yet (as at library versions in Ubuntu 12.04).

The best I've managed is to leave an empty container in the Glade file and add the widget to that programmatically.

---

