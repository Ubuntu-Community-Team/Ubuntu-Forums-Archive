---
title: "Lots of Problems with Glade 3.4.0 and C++"
date: 2008-02-22
forum: Programming Talk
---

### Post by GenuineXP on 2008-02-22
Ugh, Glade 3 isn't working at all. I'm just trying to test a small program just to preview the GUIs look and feel, but everything is messed up. Everything compiles, but when I run my program I get critical errors about not being able to set Notebook labels (I removed the default labels and added a HBox, Image, and Label instead).

The auto signal connect never seems to work, and neither does doing it explicitly! Closing the main window leaves my program hanging in the terminal! In fact, nothing happened until I explicitly told the top level window to show itself. That doesn't seem right, especially since I've never seen that in other code/tutorials.

I'm compiling with:

```
g++ db.cpp -o db $(pkg-config --cflags --libs gtk+-2.0 libglade-2.0 gmodule-2.0)
```

Here's one of the warning about the Notebook labels:

```
(db:8539): Gtk-CRITICAL **: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed
```

My one and only signal handler is decleared extern "C". This has worked for me before (my first little Glade test), but not now. I don't understand the inconsistent behaviour. I thought Glade was easier to use than *this*! :p

Not only that, but the Notebooks are all messed up. The contents of one tab are displayed by another tab is opened, and random tabs are missing! Any ideas what I'm doing wrong?

Thanks!

(btw, please don't just tell me to use Python instead.)

---

### Post by GenuineXP on 2008-02-22
I'd also like to mention that separators in my menus simply display their names instead of separators! Icons I customized are much larger than normal also, and I can't seem to change this. The display in Glade is much different than at runtime...

---

