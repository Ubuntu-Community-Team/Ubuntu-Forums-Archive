---
title: "Glade: how do I dynamically add widgets?"
date: 2009-11-19
forum: Programming Talk
---

### Post by King_Critter on 2009-11-19
So, I just learned how to use Glade, and it's pretty awesome. There's just one thing I can't figure out: how do I dynamically add content to the GUI I make with Glade?

Example: I've got some stuff in an sqlite database. Before learning glade, when I was doing the GTK code by hand, I just looped through the database, creating widgets as needed.

I can't figure out how to do this with Glade, however. 

Any hints or nudges in the right direction would be much appreciated. ^_^

---

### Post by Can+~ on 2009-11-19
You can still do it through code. Or use TreeViews/ListViews, which is more "sane", in the sense that generating widgets on runtime can lead to unexpected behavior (eg. replacing something, inserting a widget out of place when you change the original layout, many types of errors.)

[COLOR="Silver"]Philosophic POV:
Usually, I think of interfaces as time-bound objects, you can configure the initial layout, but this won't change during runtime, and the only thing that can keep track of changes in time are things that add a new dimension, such as ListViews and TreeViews.[/COLOR]

---

### Post by King_Critter on 2009-11-19
Hey, thanks for the quick reply. 

As it turns out, however, I just didn't understand the code I was writing. :P

After I realized I needed to use the "get_widget" method of the widget tree, everything fell into place. 

It's called a widget tree, right? I'm just sort of guessing, because all the tutorials I found assigned "gtk.glade.XML( "main.glade" )" the the variable "wTree", so I'm just assuming the "w" stands for widget. o_0

---

