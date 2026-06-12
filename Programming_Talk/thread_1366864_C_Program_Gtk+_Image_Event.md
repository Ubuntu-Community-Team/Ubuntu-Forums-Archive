---
title: "C Program Gtk+ Image Event"
date: 2009-12-28
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-28
I am writing a GTK+ C Program and want to call a function when an image is clicked, basically I want the image to act like a button.  Here is basically what I want to do:

```
image = gtk_image_new_from_file ("image.png");
g_signal_connect (G_OBJECT (image), "clicked", G_CALLBACK (callback), NULL);
gtk_widget_show (image);

```I quickly learned that you can't do this with a GtkImage, so I tried to use an event box:

```
event_box = gtk_event_box_new ();
g_signal_connect (G_OBJECT (event_box), "clicked", G_CALLBACK (callback), NULL);
gtk_container_add (GTK_CONTAINER (window), event_box);
gtk_widget_show (event_box);

image = gtk_image_new_from_file ("image.png");
gtk_container_add (GTK_CONTAINER (event_box), image);
gtk_widget_show (image);
```This did not work either, how can I make an image call a function when it is clicked?

---

### Post by kwyto on 2009-12-29
don't know about GTK+, but in Visual C++, for example, there is a function that tells you if the mouse has been clicked, that combined with the position of the mouse can tell you if the picture's area was clicked. have you tried searching in the web? or maybe the forums? a lot of times your problem has happened to someone else.

---

### Post by SledgeHammer_999 on 2009-12-29
link to tutorial example-->[http://library.gnome.org/devel/gtk-tutorial/stable/c1228.html#SEC-EVENTBOX](http://library.gnome.org/devel/gtk-tutorial/stable/c1228.html#SEC-EVENTBOX)

Basically you need to call gtk_widget_set_events() on the event box and set which events you want it to receive.

EDIT: also you could use an image with a GtkButton and not display a label....

---

### Post by lewisforlife on 2009-12-29
> **kwyto said:**
> don't know about GTK+, but in Visual C++, for example, there is a function that tells you if the mouse has been clicked, that combined with the position of the mouse can tell you if the picture's area was clicked. have you tried searching in the web? or maybe the forums? a lot of times your problem has happened to someone else.

Finding the position of the mouse cursor would not help me with this problem, because I am not putting my image in a fixed location, it is inside of a GtkTable which can move around.

Anyway's, I found an answer finally, if anyone else is having this issue, take a look at: [http://www.justlinux.com/forum/archive/index.php/t-132908.html](http://www.justlinux.com/forum/archive/index.php/t-132908.html)

---

