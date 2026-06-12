---
title: "GtkBuilder and &quot;names&quot;"
date: 2011-11-24
forum: Programming Talk
---

### Post by SIGTERMer on 2011-11-24
Hi, I've been trying to get the "names" of all GtkWidgets in a GtkBuilder object.

I've managed to get all objects from the builder object via gtk_builder_get_objects() and store them in a GSList.

However, when I use gtk_widget_get_name() on the gobjects (which i cast to GtkWidgets), I get generic names such as "GtkWindow" and "GtkButton" instead of "window1" or "button1" that are displayed in glade.

**Any** help would be extremely appreciated and would make this sleepy programmer **very** happy.

---

### Post by SIGTERMer on 2011-11-24
solution is here: [http://stackoverflow.com/questions/8263756/gtkbuilder-and-names](http://stackoverflow.com/questions/8263756/gtkbuilder-and-names)

---

### Post by crdlb on 2011-11-25
I believe you need to use gtk_buildable_get_name to get the GtkBuilder ID.

This was apparently changed a few years ago: [https://bugzilla.gnome.org/show_bug.cgi?id=591085](https://bugzilla.gnome.org/show_bug.cgi?id=591085)

---

### Post by SIGTERMer on 2011-11-25
Thank you!

Using the gtkBuildable interface did indeed do the trick. It's not too late to back out of a very painful and horrible design decision.

Your advice came just in time :)

---

