---
title: "[Gtkmm] How is this widget/class called?"
date: 2010-08-19
forum: Programming Talk
---

### Post by kahumba on 2010-08-19
Hi,
please see screenshot for an example, it's a widget with an image and an arrow beside it so by clicking on the arrow a drop-down list is supposed to come up. I don't know the name of this widget (class) so can't google for it to find out how to create and use it.

---

### Post by PaulM1985 on 2010-08-19
The only thing that I can find which is near is the FileChooserButton:
[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1FileChooserButton.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1FileChooserButton.html)

But I think this will start off a dialog to select a file, rather than give you a drop down list.  Do you know that the thing you require is from gtkmm?

Paul

---

### Post by kahumba on 2010-08-19
One can find these types of widgets in Nautilus as well - both the back and forward buttons each have an arrow (to choose exactly where back or forward one wanna go).

---

### Post by PaulM1985 on 2010-08-20
Found it!  I think you are after a Gtk::Toolbar with a Gtk::ToolButton.  I found this on the normal gtk site:

[http://library.gnome.org/devel/gtk/unstable/ch02.html](http://library.gnome.org/devel/gtk/unstable/ch02.html)

which is a gallery of all gtk widgets.  The image you were after was on there.  Clicking on it took me to this page:

[http://library.gnome.org/devel/gtk/unstable/GtkToolbar.html](http://library.gnome.org/devel/gtk/unstable/GtkToolbar.html)

so I just searched for GtkToolbar in gtkmm.

[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Toolbar.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Toolbar.html)

I hope this is what you wanted.

Paul

---

### Post by kahumba on 2010-08-20
Thanks, it's Gtk::MenuToolButton.

---

