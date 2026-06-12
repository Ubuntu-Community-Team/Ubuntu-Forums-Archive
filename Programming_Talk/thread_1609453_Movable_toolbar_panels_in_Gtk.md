---
title: "Movable toolbar panels in Gtk"
date: 2010-10-30
forum: Programming Talk
---

### Post by Tony Flury on 2010-10-30
Has anyone built movable toolbar panels in Gtk.

I have this idea for an Application which will support a variety of functional  Groups and plugins, and it would be nice/good/cool/useful to be able to give the user the group their own functionality buttons into moveable toolbar panels - which the user can fill how ever they wish, and which could be enabled/created/modified at will.

Has anyone done this, and is happy to give a pointer or two - for instance which GTK elements/object classes I should be using. Is there a class in GTK which creates these sort of toolbar panels ?

I don't want the full code - just a pointer in the right direction.

---

### Post by Tony Flury on 2010-11-01
Done a lot more digging, and it seems that no such thing exists in Gnome/GTK - and that if i wanted such a thing i would need to do a lot of code wrap myself - is that the case ?

---

### Post by johnl on 2010-11-01
I think all you need to do is create a HandleBox and then stuff your ToolBar into that.

Here is a python example:

```

#!/usr/bin/env python

import gtk

class MainWindow(gtk.Window):
    def __init__(self):
        super(MainWindow, self).__init__()
        
        vbox = gtk.VBox()
        handlebox = gtk.HandleBox()

        self.add(vbox)        
        vbox.pack_start(handlebox, False, False, 4)
        
        toolbar = gtk.Toolbar()
        toolbar.set_orientation(gtk.ORIENTATION_HORIZONTAL)
        toolbar.set_border_width(4)
        
        # just add some useless buttons to our toolbar
        toolbar.add(gtk.ToolButton(gtk.STOCK_NEW))
        toolbar.add(gtk.ToolButton(gtk.STOCK_OPEN))
        toolbar.add(gtk.ToolButton(gtk.STOCK_SAVE))
        toolbar.add(gtk.ToolButton(gtk.STOCK_QUIT))

        # I found if you dont set a minimum width for the toolbar
        # when you detach it, it will shrink to just a menu basically
        toolbar.set_size_request(300, 36)

        # the trick is just to put our toolbar inside the handlebox
        handlebox.add(toolbar)

        vbox.show_all()

        self.set_size_request(300, 200)

if __name__ == "__main__":
    w = MainWindow()
    w.show()
    gtk.main()

```

---

### Post by Tony Flury on 2010-11-01
Thank you so much.

---

### Post by Tony Flury on 2010-11-03
johnl - this produces panels that are tearable - which does look cool, but when i try it with multiple panels (Handleboxes) in an HBox (so that each panel can be torn off independently - that have to be docked back in the same position - i.e. the user can't re-order the toolbar.

Is there anything that would allow panels in toolbars to be shuffled around by the user ?

---

### Post by johnl on 2010-11-03
Hey Tony,

I didn't think of that -- I'm not sure.  I did a quick googling and couldn't come up with anything.

You might try asking on (one of?) the gtk mailing lists or someplace like stackoverflow.com.

---

