---
title: "how do you find the grid coordinates in a gtk+ widget"
date: 2012-08-01
forum: Programming Talk
---

### Post by linuxlover42 on 2012-08-01
Hello, I've recently started working with GTK+ for a very important project. Is there a way to get the grid coordinates of a widget within a given grid? I need this in order to determine which entry field is next to a given button (the number of buttons and entry fields of this type vary), and modify the field accordingly.

I am writing the program in C and I need an answer rather urgently so any help is appreciated. If there is another way to do it I'm fine with  that as well.

Thanks in advance.

---

### Post by Vaphell on 2012-08-02
not that i have any experience with gtk but gtk_container_child_get_property() should be able to extract top-attach, left-attach, height, width of the child widget

```
void                gtk_container_child_get_property    (GtkContainer *container,
                                                         GtkWidget *child,
                                                         const gchar *property_name,
                                                         GValue *value);
container :
	a GtkContainer

child :
	a widget which is a child of container

property_name :
	the name of the property to get

value :
	a location to return the value
```

[http://developer.gnome.org/gtk3/3.5/GtkContainer.html#gtk-container-child-get-property](http://developer.gnome.org/gtk3/3.5/GtkContainer.html#gtk-container-child-get-property)

```
Child properties

  "height"                   gint                  : Read / Write
  "left-attach"              gint                  : Read / Write
  "top-attach"               gint                  : Read / Write
  "width"                    gint                  : Read / Write
```

[http://developer.gnome.org/gtk3/3.5/GtkGrid.html](http://developer.gnome.org/gtk3/3.5/GtkGrid.html)

---

