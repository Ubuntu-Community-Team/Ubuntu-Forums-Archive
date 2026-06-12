---
title: "python/gtk - no image with stock gtk.ImageMenuItem?"
date: 2010-10-15
forum: Programming Talk
---

### Post by johnl on 2010-10-15
Hey guys,

I decided to branch out and sharpen up my python skills.  I'm doing some GTK development and I wanted to add a stock menu item to my File menu, along with the stock image.

Following what I see on the internet, I have the following:

```

    # where self is a gtk.Window

    # top level menu bar
    mb = gtk.MenuBar()

    # file menu
    menu  = gtk.Menu()
    filem = gtk.ImageMenuItem("_File")
    filem.set_submenu(menu)    

    agr = gtk.AccelGroup()
    self.add_accel_group(agr)

    newi = gtk.ImageMenuItem(gtk.STOCK_NEW, agr)
    key, mod = gtk.accelerator_parse("N")
    newi.add_accelerator("activate", agr, key, mod, gtk.ACCEL_VISIBLE)
    menu.add(newi)

    menu.show_all()
    mb.add(filem)

```

The result is that I get the menu as expected, complete with accelerator keys, but no stock image next to it.

I even tried adding:

```

    newi.set_image(gtk.image_new_from_stock(gtk.STOCK_NEW, gtk.IMAGE_SIZE_MENU))

```

to no avail.


Any suggestions?

---

### Post by johnl on 2010-10-15
In case anyone was wondering, the problem was simple -- gnome was configured not to show icons in menus. whoops.

I turned the gconf key /desktop/gnome/interface/menus_have_icons and voila, works as expected.

---

### Post by nvteighen on 2010-10-15
> **johnl said:**
> In case anyone was wondering, the problem was simple -- gnome was configured not to show icons in menus. whoops.

I turned the gconf key /desktop/gnome/interface/menus_have_icons and voila, works as expected.

Yeah, I was wondering! But didn't reply because I was absolutely confused by this... LOL...

Glad to hear you solved it.

---

