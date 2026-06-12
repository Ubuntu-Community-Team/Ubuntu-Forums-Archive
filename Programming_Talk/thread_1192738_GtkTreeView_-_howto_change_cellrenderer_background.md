---
title: "Gtk::TreeView - howto change cell/renderer background"
date: 2009-06-20
forum: Programming Talk
---

### Post by froggyswamp on 2009-06-20
Folks,
I think the cell renderer is what I need to change properties (like the background) of a cell in a Gtk::TreeView, but I can't figure out how to do it.
If needed, here's my code that creates/adds the renderer:
```

Gtk::TreeView::Column *pColumn = Gtk::manage(new Gtk::TreeView::Column("Name"));
Gtk::CellRendererText *pNameRend = new Gtk::CellRendererText();

pColumn->pack_start(*pNameRend, true);
pColumn->add_attribute(pNameRend->property_text(), treeModelCR.colName);
append_column(*pColumn);

```

Any link or ideas please?

---

### Post by monraaf on 2009-06-20
[PHP]
cellrenderer.set_property("cell-background","magenta")
[/PHP]

Or something equivalent with whatever gtkmm has to offer.

---

### Post by froggyswamp on 2009-06-20
Thanks!!

May I know (a link would be nice) where do you know from about "cell-background" and other keys?  (any other detail is also welcome)

To get C++ to compile:
```

Glib::ustring sKey = "cell-background";
Glib::ustring sVal = "magenta";
pNameRend->set_property(sKey, sVal);

```

---

### Post by monraaf on 2009-06-20
Since I do my GUI stuff mainly in Python, I usually get the info from the excellent API reference at: [http://www.pygtk.org/docs/pygtk/index.html](http://www.pygtk.org/docs/pygtk/index.html)

Bu I do occasionally peek at  the C API reference.

[http://library.gnome.org/devel/gtk/stable/GtkCellRenderer.html#GtkCellRenderer.properties](http://library.gnome.org/devel/gtk/stable/GtkCellRenderer.html#GtkCellRenderer.properties)

---

### Post by froggyswamp on 2009-06-20
Thanks again, I noticed that there's (much) more Python/Gtk documentation than C++/Gtk, in fact, the only (half) complete documentation/tutorial is on the Gtkmm site. There's nothing like the (huge and very useful to me) "The Java Tutorial" that I used to learn from when I was learning Java. It covered practically everything I needed, not just basic stuff.

---

