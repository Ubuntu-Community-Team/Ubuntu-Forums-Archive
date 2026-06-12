---
title: "GTK get widget child"
date: 2011-09-17
forum: Programming Talk
---

### Post by nickos on 2011-09-17
How can i get the child of a widget in GTK+ ?

---

### Post by SledgeHammer_999 on 2011-09-17
If a widget A has child widgets then it is a [GtkContainer](http://developer.gnome.org/gtk3/stable/GtkContainer.html) also. So you could use [gtk_container_get_children()](http://developer.gnome.org/gtk3/stable/GtkContainer.html#gtk-container-get-children)

---

