---
title: "understanding  PyGtk"
date: 2009-10-26
forum: Programming Talk
---

### Post by baskar007 on 2009-10-26
I am pretty new to Gtk.I have read many examples, but still i can't figure out looping method. 

i want to show the realtime changes of local variables on GUI.

for examble:
i have a variable named SIZE.  SIZE="slim"
this SIZE variable will change it's value every 1sec.

how can i show it's changes in GUI using pyGtk?

i think this a chilly question for you. But i little more confused :(with PyGTK, i need some guide so please help me.

---

### Post by SledgeHammer_999 on 2009-10-26
(I don't know python)

Use a GtkLabel. And then update the text it shows with gtklabel.set_label(SIZE)

---

### Post by nvteighen on 2009-10-26
This is a fairly complex issue... A way to solve it is to use the Model View Controller design in order to simulate a "real time" update by redrawing the desired label on demand... to do that in a sane way takes a lot of knowledge... 

Another way is to use multiple threads, which is also a difficult thing to master and I guess that interfering with GTK+'s own multithreading may also be complicated...

Conclusion: This has nothing to do with "understanding GTK+", but with the difficult topic of how to deal with non-sequential instructions in computing.

---

### Post by EndOn9 on 2009-10-27
Maybe [this]("http://www.pygtk.org/pygtk2reference/gobject-functions.html#function-gobject--timeout-add") might prove helpful :)

---

### Post by baskar007 on 2009-10-28
> **EndOn9 said:**
> Maybe [this]("http://www.pygtk.org/pygtk2reference/gobject-functions.html#function-gobject--timeout-add") might prove helpful :)
thank you

---

