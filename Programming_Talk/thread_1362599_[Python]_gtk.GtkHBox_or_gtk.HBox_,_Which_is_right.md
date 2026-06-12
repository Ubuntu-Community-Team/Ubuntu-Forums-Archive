---
title: "[Python] gtk.GtkHBox or gtk.HBox , Which is right?"
date: 2009-12-23
forum: Programming Talk
---

### Post by baskar007 on 2009-12-23
Hi friends,
     I am newbie to GTK, I have an idea to write a python application on GTk GUI. i am using Ubuntu9.10 with python 2.6 minimal. 
I refered tutorials on [http://www.pygtk.org/tutorial.html](http://www.pygtk.org/tutorial.html)  .

in this tutorial examples the GTk window given as like this

```

window = gtk.GtkWindow(gtk.WINDOW_TOPLEVEL)
hbox = gtk.GtkHBox(gtk.FALSE, 5)

```

but i am getting errors when i run these codes.

```

unhandled AttributeError
"'module' object has no attribute 'GtkWindow'"

unhandled AttributeError
"'module' object has no attribute 'GtkHBox'"

```

after that i tried same codes with little changes 

```

window = gtk.Window(gtk.WINDOW_TOPLEVEL)
hbox = gtk.HBox(gtk.FALSE, 5)

```

which one is the right code on above two?

is that tutorial is wrong? or module problem in my PC?

---

### Post by Can+~ on 2009-12-23
I think you were reading the PyGTK 0.6.x (GTK+ 1.x) tutorial, you should read the newer one.

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

Also, take a look at glade:

```
sudo apt-get install glade
```

---

### Post by nvteighen on 2009-12-23
Drop the Gtk* prefix everywhere you see it. It makes no sense in the OOP nature of Python to use qualified names (like GTK+ does in C).

---

### Post by baskar007 on 2009-12-23
Thank you.

---

