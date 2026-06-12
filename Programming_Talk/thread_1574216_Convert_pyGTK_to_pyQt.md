---
title: "Convert pyGTK to pyQt"
date: 2010-09-13
forum: Programming Talk
---

### Post by glilco on 2010-09-13
I need to convert a code writen with pyGTK to pyQt. This is needed because the code will be executed in a netbook with a very small HD and I will use kubuntu netbook edition.

Can anyone help me to "translate" the code?

```
#
# Copyright 2009 Canonical Ltd.
#
# Authors: Neil Jagdish Patel <neil.patel@canonical.com>
#          Jono Bacon <jono@ubuntu.com>
#          Paulo Schreiner <paulo.schreiner@gmail.com>
#          Murilo Ferraz Franco <muriloffranco@gmail.com>
#
# This program is free software: you can redistribute it and/or modify it 
# under the terms of either or both of the following licenses:
#
# 1) the GNU Lesser General Public License version 3, as published by the 
# Free Software Foundation; and/or
# 2) the GNU Lesser General Public License version 2.1, as published by 
# the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranties of 
# MERCHANTABILITY, SATISFACTORY QUALITY or FITNESS FOR A PARTICULAR 
# PURPOSE.  See the applicable version of the GNU Lesser General Public 
# License for more details.
#
# You should have received a copy of both the GNU Lesser General Public 
# License version 3 and version 2.1 along with this program.  If not, see 
# <http://www.gnu.org/licenses/>
#

import gobject
import gtk
import appindicator
import os

def callback(widget, data):
    print "Hello Again - %s was pressed" % data
    os.system("xrandr --output LVDS1 %s" % data)

if __name__ == "__main__":
  ind = appindicator.Indicator ("example-simple-client",
                              "gsd-xrandr",
                              appindicator.CATEGORY_APPLICATION_STATUS)
  ind.set_status (appindicator.STATUS_ACTIVE)
  ind.set_attention_icon ("gsd-xrandr")

  # create a menu
  menu = gtk.Menu()

  # create some 

  buf = "Normal (800x480)"

  menu_items = gtk.MenuItem(buf)
  menu.append(menu_items)

    # this is where you would connect your menu item up with a function:
  menu_items.connect("activate", callback, "--scale 1x1 --panning 0x0")

    # show the items
  menu_items.show()

  #for i in range(3):
  buf = "Esticado (1024x615)"

  menu_items = gtk.MenuItem(buf)
  menu.append(menu_items)

    # this is where you would connect your menu item up with a function:
  menu_items.connect("activate", callback, "--scale 1.28x1.28 --panning 0x0")

    # show the items
  menu_items.show()

  buf = "Esticado (1200x720)"

  menu_items = gtk.MenuItem(buf)
  menu.append(menu_items)

    # this is where you would connect your menu item up with a function:
  menu_items.connect("activate", callback, "--scale 1.5x1.5 --panning 0x0")

    # show the items
  menu_items.show()  

    # show the items
  menu_items.show()
  buf = "Virtual (104x768)"

  menu_items = gtk.MenuItem(buf)
  menu.append(menu_items)

    # this is where you would connect your menu item up with a function:
  menu_items.connect("activate", callback, "--scale 1x1 --panning 1024x768")

    # show the items
  menu_items.show()


  ind.set_menu(menu)

  gtk.main()
```

---

### Post by nvteighen on 2010-09-14
> **glilco said:**
> I need to convert a code writen with pyGTK to pyQt. This is needed because the code will be executed in a netbook with a very small HD and I will use kubuntu netbook edition.

Can anyone help me to "translate" the code?


There's no real need to do that. GTK+ can be used on KDE without installing GNOME at all, but just libgtk-2.0 and its dependencies, which should be a couple of MB... If the netbook is going to use Kubuntu, I don't think its HD to be that small to run out of space because of installing GTK+.

---

### Post by glilco on 2010-09-14
The HD haves less than 4GB. A couple of MB makes a lot of difference. I will try to install libgtk-2.0. thanks

---

