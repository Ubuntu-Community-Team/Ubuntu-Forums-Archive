---
title: "GTK+ newbie doubt regarding buttons"
date: 2010-12-11
forum: Programming Talk
---

### Post by jfreak_ on 2010-12-11
How do I put an image as a child widget of a button(without using glade)? I want my button to have a custom image on it instead of text. Also is it possible to change and remove the image during runtime?

---

### Post by dv3500ea on 2010-12-11
This code is pygtk, but it should be similar for gtk for any language:

```

button = gtk.Button()
container = gtk.HBox()
button.add(container)
container.show()
image = gtk.Image()
image.set_from_file('some_image_path')
image.show()
label = gtk.Label(' <-- Nice image')
label.show()
container.add(image)
container.add(label)
button.show()

```

---

### Post by SledgeHammer_999 on 2010-12-11
Use the [gtk_button_set_image()](http://library.gnome.org/devel/gtk/stable/GtkButton.html#gtk-button-set-image) function.

---

### Post by jfreak_ on 2010-12-11
Thanks

Another thing, is there any way to remove the internal padding between the button widget and the image?
PS: I use C

---

### Post by SledgeHammer_999 on 2010-12-11
A GtkButton derives from GtkContainer. So try playing with this function [gtk_container_set_border_width()](http://library.gnome.org/devel/gtk/stable/GtkContainer.html#gtk-container-set-border-width).

Sample code:
[php]
// 'myButton' is a variable of type 'GtkButton*'
gtk_container_set_border_width(GTK_CONTAINER(myButton), 0);
[/php]

---

