---
title: "Fun with Gtk window borders"
date: 2009-09-25
forum: Programming Talk
---

### Post by froggyswamp on 2009-09-25
Folks, I noticed that when setting the border width on a window < 0 and a size request with at least one param of -1 the window starts looking very weird.

```

gtk_container_set_border_width(GTK_CONTAINER(window), -1);
//in next line remove -1 with >=0 and you get the normal window back
gtk_widget_set_size_request(window, 200, -1);

```

just for fun
even if it's a bug I don't think anyone will care fixing it.

---

### Post by SledgeHammer_999 on 2009-09-25
from->[http://library.gnome.org/devel/gtk/stable/GtkContainer.html#gtk-container-set-border-width](http://library.gnome.org/devel/gtk/stable/GtkContainer.html#gtk-container-set-border-width)

> border_width : amount of blank space to leave outside the container. **Valid values are in the range 0-65535 pixels.** 

I think they have forgotten to check if border_width is between 0 and 65535

---

