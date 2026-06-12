---
title: "What is the GTK equivalent of Windows WM_INITDIALOG?"
date: 2009-07-06
forum: Programming Talk
---

### Post by resander on 2009-07-06
WM_INITDIALOG is a Windows dialog message/event that is emitted immediately before a dialog box is displayed. It is typically used for setting initial values for the widgets in the dialog.

What is the equivalent signal/event in GTK?

---

### Post by nrs on 2009-07-06
maybe 
[http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-realize](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-realize)
[http://www.gtk.org/api/2.6/gtk/GtkWidget.html#gtk-widget-realize ]("http://www.gtk.org/api/2.6/gtk/GtkWidget.html#gtk-widget-realize")
I override on_realize in GTKmm to accomplish this, at least. No idea whether it's considered bad practice.

---

### Post by Can+~ on 2009-07-06
In GTK, you usually do all the set up, and when it's ready, you call the show() (or show_all()) method to present everything done.

---

### Post by nvteighen on 2009-07-06
> **Can+~ said:**
> In GTK, you usually do all the set up, and when it's ready, you call the show() (or show_all()) method to present everything done.
Yeah... GTK+ tends to do that: prepare stuff at "backstage" and then show it. IMO, it's cleaner than using a separate event for that.

---

### Post by nrs on 2009-07-06
Well, it all depends on whether you're using a custom dialog/widget or not, IMO. If it's stock, then yeah, I agree.

---

### Post by resander on 2009-07-07
Thanks for responses...

A fine point maybe, but on balance I prefer a separate event, because it allows me to concentrate on the presentation of the dialog first without having to worry about the data.

This application shows records from a database. The user generates event 'show record n' via the GUI and this causes the widgets in the dialog to show the fields of record n. The logic that builds the dialog would have to generate 'show first record' event internally. Lexically/physically decoupling presentation from program logic seems better.

---

### Post by nvteighen on 2009-07-07
> **resander said:**
> Thanks for responses...

A fine point maybe, but on balance I prefer a separate event, because it allows me to concentrate on the presentation of the dialog first without having to worry about the data.

This application shows records from a database. The user generates event 'show record n' via the GUI and this causes the widgets in the dialog to show the fields of record n. The logic that builds the dialog would have to generate 'show first record' event internally. Lexically/physically decoupling presentation from program logic seems better.

I fail to see why our advices would go against decoupling presentation and program logic... unless your database interface is not well designed.

If you've got a procedure that polls the nth record from the database, just use it to poll the first one and show the dialog. There's no interface-implementation mess here! You're using your own interface, something you're supposed to do! Ok, maybe you'll have to reorder your data to fit into the GTK+ data structures, but that sort of "glue code" is interface-side and unavoidable...

Something really bad would be that you coded your polling function in between the GUI code...

A good test to do is the following. Take your code and mentally (or physically, under your own risk) remove the whole GUI code. Now see whether it's possible to code (or actually code!) a command line interface for it without modifying anything else. If you can, your program is modularized and there's no presentation/code coupling. If not, something is wrong.

---

