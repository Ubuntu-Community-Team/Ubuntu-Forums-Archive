---
title: "glade-3 tutorial?"
date: 2007-07-02
forum: Programming Talk
---

### Post by slavik on 2007-07-02
Is anyone aware of any tutorials that show how to use Glade3 generated file with libglade using C (with callbacks and grabbing other widgets).

NOTE to python fanboys: I am not looking for PyGTK or Python, I want C and C only. Thank you.

---

### Post by maddog39 on 2007-07-02
As far as I know almost nobody uses Glade with C, which is why there arent really any tutorials for it. Here are some things (tutorials and code examples) I found from googling:

[http://www.micahcarrick.com/v2/content/view/13/3/](http://www.micahcarrick.com/v2/content/view/13/3/)
[http://adammonsen.com/tut/libgladeTest.html](http://adammonsen.com/tut/libgladeTest.html)
[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s02.html](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s02.html)
[http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html](http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html)

I think most of these are for Glade 2 but I think everything is backward compatible, and they really just added a bunch of new features and widgets and what not.

---

### Post by spacemoose on 2009-04-13
Wow, you didn't get a lot of responses.  You've probably moved on and are in a position to write a tutorial now.  But for those individuals who get here by searching for something similar, Micheal Carrick did do a glade 3 tutorial.  He shows how to do both C and Python, but your choice of language shouldn't be too important.

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by rich1939 on 2009-04-13
> **slavik said:**
> Is anyone aware of any tutorials that show how to use Glade3 generated file with libglade using C (with callbacks and grabbing other widgets).

NOTE to python fanboys: I am not looking for PyGTK or Python, I want C and C only. Thank you.

There's a fairly good tutorial in the "Foundations of GTK Development" book by Andrew Krause (Chapter-8 ). The entire book is devoted to C and Gtk+ development.

And, BTW, libglade is deprecated in favor of using GtkBuilder. The GLADE file can be easily converted using the **gtk-builder-convert** command. The widgets you develop with Glade can then be accessed using statements similar to the following:

```

GtkWidget *window;

	window = GTK_WIDGET(gtk_builder_get_object (builder, "window"));
	gtk_builder_connect_signals(builder, NULL);
	gtk_widget_show_all (window);

```

---

### Post by Squigy Dunkens on 2009-04-13
> **maddog39 said:**
> As far as I know almost nobody uses Glade with C, which is why there arent really any tutorials for it. Here are some things (tutorials and code examples) I found from googling:

[http://www.micahcarrick.com/v2/content/view/13/3/](http://www.micahcarrick.com/v2/content/view/13/3/)
[http://adammonsen.com/tut/libgladeTest.html](http://adammonsen.com/tut/libgladeTest.html)
[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s02.html](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s02.html)
[http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html](http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html)

I think most of these are for Glade 2 but I think everything is backward compatible, and they really just added a bunch of new features and widgets and what not.

The micah carrick one is in glade 3

---

### Post by days_of_ruin on 2009-04-13
> **rich1939 said:**
> There's a fairly good tutorial in the "Foundations of GTK Development" book by Andrew Krause (Chapter-8 ). The entire book is devoted to C and Gtk+ development.

And, BTW, libglade is deprecated in favor of using GtkBuilder. The GLADE file can be easily converted using the **gtk-builder-convert** command. The widgets you develop with Glade can then be accessed using statements similar to the following:

```

GtkWidget *window;

	window = GTK_WIDGET(gtk_builder_get_object (builder, "window"));
	gtk_builder_connect_signals(builder, NULL);
	gtk_widget_show_all (window);

```

With the latest version of glade converting is no longer necessary.

---

### Post by rich1939 on 2009-04-13
> **days_of_ruin said:**
> With the latest version of glade converting is no longer necessary.

When is that version of Glade going to be in the Ubuntu repositories?

---

### Post by days_of_ruin on 2009-04-13
> **rich1939 said:**
> When is that version of Glade going to be in the Ubuntu repositories?

Not sure if it will ever be in intrepid but its in jaunty;)

---

### Post by slavik on 2009-04-13
What a blast from the past ... we've all moved on from that.

OP, message me if you want this thread re-opened (not likely to happen) ... heh.

EDIT: there was no need to resurrect this.

---

