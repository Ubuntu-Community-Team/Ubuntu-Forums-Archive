---
title: "How to do this in GTK?"
date: 2009-11-12
forum: Programming Talk
---

### Post by blazemore on 2009-11-12
Look at the screenshot, specifically at the large table with the tone names and values in them. Is there a way I can do this in GTK (With a resizable column) I'm using Glade and I can't find anything that looks like this.

---

### Post by froggyswamp on 2009-11-12
Where is your screenshot

---

### Post by blazemore on 2009-11-12
whoops lol
here it is

---

### Post by froggyswamp on 2009-11-12
I'm also learning Gtk (but in pure C). That app doesn't have anything special.
The "table" thing in Gtk is called a GtkTreeView, you can add as many columns as you wish:
[http://library.gnome.org/devel/gtk/unstable/GtkTreeView.html](http://library.gnome.org/devel/gtk/unstable/GtkTreeView.html)
I have to admit that GtkTreeView is probably the most sophisticated widget in Gtk.
Glade should have an option to create a GtkTreeView (sorry not using Glade so don't know exactly how to).

---

### Post by blazemore on 2009-11-13
I added that and it asked for a data model or something. I haven't done any UML! I'm trying to clone this application in Python/GTK. The rows depend on user input.

---

### Post by froggyswamp on 2009-11-13
I guess you can google for GtkTreeView. Alternatively, there's a book "Foundations of Gtk Development" (2007), there's a whole chapter dedicated to GtkTreeView and its (2 types of) models, I could borrow the pdf version.

---

### Post by kostkon on 2009-11-13
You could check [this blog post]("http://tadeboro.blogspot.com/2009/09/glade3-tutorial-4-gtktreeview-data.html"). It's part of a tutorial on Glade.

Hope that helps.

---

