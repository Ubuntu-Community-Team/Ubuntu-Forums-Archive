---
title: "[vala/gtk] Button with menu"
date: 2010-02-23
forum: Programming Talk
---

### Post by Sublime Porte on 2010-02-23
Howdy,

Does anyone know if there's a button widget with a drop down menu available in gtk? Something like the QToolButton from Qt (with default behaviour, not the arrow). I am using genie/vala which I assume has all the standard gtk widgets available. Can't seem to find one in the documentation.

---

### Post by nowic on 2010-09-16
Better late than never... ;-)

The widget is called Gtk.ComboBox:

[http://valadoc.org/gtk+-2.0/Gtk.ComboBox.html](http://valadoc.org/gtk+-2.0/Gtk.ComboBox.html)

```

var chooser = new ComboBox.text ();
chooser.append_text ("First option");
chooser.append_text ("Second option");
chooser.changed.connect ((widget) => {
    if (widget.get_active () == 0) {
        // Do option 1
    } else {
        // Do option 2
    }
});

```

---

### Post by SledgeHammer_999 on 2010-09-17
I think you're looking for [GtkMenuToolButton](http://library.gnome.org/devel/gtk/stable/GtkMenuToolButton.html)

---

