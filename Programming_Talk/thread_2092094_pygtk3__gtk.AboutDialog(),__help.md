---
title: "pygtk3  gtk.AboutDialog(),  help"
date: 2012-12-06
forum: Programming Talk
---

### Post by yanes on 2012-12-06
Salam all , 
in my python and pygtk3  program , I want to set an icon in the about dialog .
 this code works in pygtk2 :
```

about = gtk.AboutDialog()
about.set_logo(gtk.gdk.pixbuf_new_from_file("icon.png"))

```

but since my project imports pygtk 3  it return the following error :
```

AttributeError: 'gi.repository.Gtk' object has no attribute 'Gdk'

```
how to get a pixbuf for my icon to display it in the about Dlg ?
and please , I need  any  pygtk 3.x APIs reference or docs
thanks in advance ):P

---

### Post by MestreLion on 2013-05-15
The problem lies in your imports and calls: 'Gdk' is not a member of 'Gtk', they are independent libraries. And 'GdkPixpuf' is another library, independent from both Gtk and Gdk. So your call 'gtk.gdk.pixbuf...' makes no sense.

The code should be:

```

from gi.repository import Gtk, GdkPixbuf
about = gtk.AboutDialog()
about.set_logo(GdkPixbuf.new_from_file("icon.png"))

```

Also note this is not **"pygtk3"**. PyGtk is a deprecated library, I'm not even sure if there is PyGtk for Gtk3+. The 'gi.repository' you're using is the new method of accessing Gnome's libs, the **gir** bindings, a merge of PyGObjetcs and PyGI. So avoid the temptation to "rename" the imports like "from gi.repository import Gtk as gtk". The upper case 'Gtk' helps telling apart from the old lowercase 'gtk' of pygtk.

There are many 'gir' bindings available, you may need to install the one for GdkPixbug. To list them all:

```
dpkg -l  gir1.2-*
```

And use **sudo apt-get install gir1.2-...** to install the ones you want/need

As for documentation, there is not much documentation on python's side, but since gir is an almost direct wrapper to the underlying C libraries, the official C docs for GdkPixbuf and Gtk can be used. You can install the **libg...-doc** packages. To list them:

```
dpkg -l  libg*-doc
```

Now you can use DevHelp to browse the documentation:

```
sudo apt-get install devhelp
```

Or, if you want an online version:

[http://www.gtk.org/documentation.php](http://www.gtk.org/documentation.php)

(PS: forum maintainers, this topic is fairly high-ranked in google searches, so I suggest it should not be closed, as info here can be helpful to many vistors)

---

