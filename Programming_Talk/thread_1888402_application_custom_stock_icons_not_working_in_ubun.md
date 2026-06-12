---
title: "application custom stock icons not working in ubuntu unity-2d top appmenu"
date: 2011-11-29
forum: Programming Talk
---

### Post by giuspen on 2011-11-29
I recently noticed that in ubuntu unity-2d the top menu of my apps does not show the (custom) icons I added to the gtk stock, but only the basic gtk stock icons.

This happens only since the top menu is displayed in the unity top panel (appmenu) and not in the application window. In place of the correct custom icons I see "gtk-missing-image". On my apps toolbars and other menus those icons are displayed properly, the problem is only with the top menu.

This happens either with pygtk2 (e.g. [http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/)) and gobject introspection (e.g. [http://www.giuspen.com/nautilus-pyextensions/](http://www.giuspen.com/nautilus-pyextensions/)). I use gtk ui manager after integrating the stock icons this way:

[PHP]factory = gtk.IconFactory()
pixbuf = gtk.gdk.pixbuf_new_from_file(filepath)
iconset = gtk.IconSet(pixbuf)
factory.add(stock_name, iconset)
factory.add_default()[/PHP]

If anybody solved this problem please help. Cheers, Giuseppe.

---

