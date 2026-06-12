---
title: "[SOLVED] C - Displaying images in window with GTK2"
date: 2008-03-29
forum: Programming Talk
---

### Post by Gibbs on 2008-03-29
I'm not really a "programmer" but fluent in some scripting. I'm using GTK2 to make a GUI application in Ubuntu. I'm using the documentation from [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) and so far things are going great with one exception.

I'm trying to draw a header/banner from a PNG with no luck. I can't find anything documented either. Any help would be greatly appreciated!

---

### Post by POW R TOC H on 2008-03-29
I'm not sure I can help (I don't have much exp. with GTK) but I can see that your question is a bit confusing...
You should post some parts (the parts you think makes the problem) of your code, people will help you faster and more accurate...
Good luck!

---

### Post by bruce89 on 2008-03-29
You're after [GtkImage]("http://library.gnome.org/devel/gtk/stable/GtkImage.html").

[PHP]
GtkWidget *image;

image = gtk_image_new_from_file ("file_name.png");
[/PHP]

It's just a normal widget, so you can pack it into boxes or add it to a container etc.

---

### Post by Gibbs on 2008-03-29
> **bruce89 said:**
> You're after [GtkImage]("http://library.gnome.org/devel/gtk/stable/GtkImage.html").

[PHP]
GtkWidget *image;

image = gtk_image_new_from_file ("file_name.png");
[/PHP]

It's just a normal widget, so you can pack it into boxes or add it to a container etc.

Ah brilliant. Didn't think it would be that simple. Thanks!

---

