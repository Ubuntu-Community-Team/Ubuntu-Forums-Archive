---
title: "Rsync in python"
date: 2012-03-12
forum: Programming Talk
---

### Post by Jenkins1 on 2012-03-12
Hello All

I am making an appindicator for myself in order to rsync my documents to my portable harddrive for myself. I am writing it in python and have learnt how to thread. Although I am not sure if I have done it correctly but it currently works.

```
from gi.repository import Gtk
from gi.repository import AppIndicator3 as appindicator
import os
import time
import threading
import subprocess

class startsync (threading.Thread):
    def run(self):
        global status
        status = "started"
        menu_items1.hide()
        menu_items2.hide()
        menu_items3.hide()
        menu_items4.hide()
        menu_items5.show()
        while status =="started":
            print "auto sync running"
            os.system("rsync -vutra --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/ /media/My\ Passport/")
            time.sleep(10)
        else:
            print "auto sync stopping"

class stopsync (threading.Thread):
    def run(self):
        global status
        status = "stopped"
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items5.hide()

class pctomypassport (threading.Thread):
    def run(self):
        menu_items1.hide()
        menu_items2.hide()
        menu_items3.hide()
        menu_items4.hide()
        menu_items5.hide()
        menu_items6.show()
        os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/ /media/My\ Passport/")
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items6.hide()
       
def menuitem_response(w, buf):
   print buf
#def __init__(self):

def my_passport_to_pc(self):
    def run(self):
        menu_items1.hide()
        menu_items2.hide()
        menu_items3.hide()
        menu_items4.hide()
        menu_items5.hide()
        menu_items6.show()
        os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /media/My\ Passport/ /home/")

def pc_to_my_passport(self):
    v = pctomypassport()
    v.start()
    """menu_items1.hide()
    menu_items2.hide()
    menu_items3.hide()
    menu_items4.hide()
    menu_items5.hide()
    menu_items6.show()
    answer = os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/luke-jennings/ /media/My\ Passport/")
    print answer
    if answer==0:
        print "done"
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items6.hide()"""

def auto_sync(self):
    t = startsync() 
    t.start()

def stop_auto_sync(self):
    u = stopsync()
    u.start()

def exit(self):
    Gtk.main_quit()

if __name__ == "__main__":
#def __init__(self):
   ind = appindicator.Indicator.new (
                        "example-simple-client",
                        "indicator-messages",
                        appindicator.IndicatorCategory.APPLICATION_STATUS)
   ind.set_status (appindicator.IndicatorStatus.ACTIVE)
   ind.set_attention_icon ("indicator-messages-new")
   ind.set_icon("/usr/share/icons/Humanity/devices/24/gnome-dev-harddisk-usb.svg")
   # create a menu
   menu = Gtk.Menu()
 
   # create some 
   
   #buf = "My Passport to PC"#"Test-undermenu - %d" % i
 
   menu_items1 = Gtk.MenuItem("My Passport to PC")
   menu_items2 = Gtk.MenuItem("PC to My Passport")
   menu_items3 = Gtk.MenuItem("Auto Sync")
   menu_items4 = Gtk.MenuItem("Exit")
   menu_items5 = Gtk.MenuItem("Stop Auto Sync")
   menu_items6 = Gtk.MenuItem("Syncing....")
   #menu.append(menu_items)
   menu.append(menu_items1)
   menu.append(menu_items2)
   menu.append(menu_items3)
   menu.append(menu_items4)
   menu.append(menu_items5)
   menu.append(menu_items6)
   # this is where you would connect your menu item up with a function:
   menu_items1.connect("activate", my_passport_to_pc)  
   menu_items2.connect("activate", pc_to_my_passport) 
   menu_items3.connect("activate", auto_sync) 
   menu_items4.connect("activate", exit) 
   menu_items5.connect("activate", stop_auto_sync) 
   # menu_items.connect("activate", menuitem_response, buf)
 
   # show the items
   menu_items1.show()
   menu_items2.show()
   menu_items3.show()
   menu_items4.show()
 
   ind.set_menu(menu)
 
   Gtk.main()


```

I am struggling with the section below, when a sync is run I want to hide the menu items except the one that says "syncing...." this part works. But the menu items are not appearing after the os.system command is run. Anyone know why?

```
class pctomypassport (threading.Thread):
    def run(self):
        menu_items1.hide()
        menu_items2.hide()
        menu_items3.hide()
        menu_items4.hide()
        menu_items5.hide()
        menu_items6.show()
        os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/ /media/My\ Passport/")
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items6.hide()
```

Thanks

---

### Post by r-senior on 2012-03-12
I think that in your imports you need:

```
from gi.repository import GObject
```

Then, at the very start of the program, you need:

```
GObject.threads_init()
```

It's basically this, but updated for Python and GTK3:

[http://unpythonic.blogspot.com/2007/08/using-threads-in-pygtk.html](http://unpythonic.blogspot.com/2007/08/using-threads-in-pygtk.html)

---

### Post by Jenkins1 on 2012-03-12
Thanks for the reply, I now get the menu changing back again when I click "PC to My Passport" but not all the items appear/disappear as appropriate, I can't see why. Also the "My Passport to PC" button does not run the "mypassporttopc" thread and I can't see why.

I have moved a couple of the menu changes around.

```
#!/usr/bin/env python
#
# Copyright 2009-2012 Canonical Ltd.
#
# Authors: Neil Jagdish Patel <neil.patel@canonical.com>
#          Jono Bacon <jono@ubuntu.com>
#          David Planella <david.planella@ubuntu.com>
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

from gi.repository import Gtk
from gi.repository import AppIndicator3 as appindicator
from gi.repository import GObject
import os
import time
import threading
import subprocess

GObject.threads_init()

class startsync (threading.Thread):
    def run(self):
        global status
        status = "started"
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items5.hide()
        menu_items6.hide()
        while status =="started":
            print "auto sync running"
            os.system("rsync -vutra --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/ /media/My\ Passport/")
            time.sleep(10)
        else:
            print "auto sync stopping"
            menu_items1.show()
            menu_items2.show()
            menu_items3.show()
            menu_items4.show()
            menu_items5.hide()
            menu_items6.hide()

class stopsync (threading.Thread):
    def run(self):
        global status
        status = "stopped"
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items5.hide()

class pctomypassport (threading.Thread):
    def run(self):
        os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /home/ /media/My\ Passport/")
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items5.show()
        menu_items6.hide()

class mypassporttopc (threading.Thread):
    def run(self):
        print "hello"
        os.system("rsync -vtura --progress --exclude-from=/media/My\ Passport/.Autorun/exclude-list.txt /media/My\ Passport/ /home")
        menu_items1.show()
        menu_items2.show()
        menu_items3.show()
        menu_items4.show()
        menu_items5.show()
        menu_items6.hide()


def menuitem_response(w, buf):
   print buf


def my_passport_to_pc(self):
    menu_items1.hide()
    menu_items2.hide()
    menu_items3.hide()
    menu_items4.hide()
    menu_items5.hide()
    menu_items6.show()
    w = mypassporttopc()
    w.start    

def pc_to_my_passport(self):
    menu_items1.hide()
    menu_items2.hide()
    menu_items3.hide()
    menu_items4.hide()
    menu_items5.hide()
    menu_items6.show()
    v = pctomypassport()
    v.start()
    

def auto_sync(self):
    t = startsync() 
    t.start()

def stop_auto_sync(self):
    u = stopsync()
    u.start()

def exit(self):
    Gtk.main_quit()

if __name__ == "__main__":
#def __init__(self):
   ind = appindicator.Indicator.new (
                        "example-simple-client",
                        "indicator-messages",
                        appindicator.IndicatorCategory.APPLICATION_STATUS)
   ind.set_status (appindicator.IndicatorStatus.ACTIVE)
   ind.set_attention_icon ("indicator-messages-new")
   ind.set_icon("/usr/share/icons/Humanity/devices/24/gnome-dev-harddisk-usb.svg")
   # create a menu
   menu = Gtk.Menu()
 
   # create some 
   
   #buf = "My Passport to PC"#"Test-undermenu - %d" % i
 
   menu_items1 = Gtk.MenuItem("My Passport to PC")
   menu_items2 = Gtk.MenuItem("PC to My Passport")
   menu_items3 = Gtk.MenuItem("Auto Sync")
   menu_items4 = Gtk.MenuItem("Exit")
   menu_items5 = Gtk.MenuItem("Stop Auto Sync")
   menu_items6 = Gtk.MenuItem("Syncing....")
   #menu.append(menu_items)
   menu.append(menu_items1)
   menu.append(menu_items2)
   menu.append(menu_items3)
   menu.append(menu_items4)
   menu.append(menu_items5)
   menu.append(menu_items6)
   # this is where you would connect your menu item up with a function:
   menu_items1.connect("activate", my_passport_to_pc)  
   menu_items2.connect("activate", pc_to_my_passport) 
   menu_items3.connect("activate", auto_sync) 
   menu_items4.connect("activate", exit) 
   menu_items5.connect("activate", stop_auto_sync) 
   # menu_items.connect("activate", menuitem_response, buf)
 
   # show the items
   menu_items1.show()
   menu_items2.show()
   menu_items3.show()
   menu_items4.show()
   menu_items5.hide()
   menu_items6.hide()

 
   ind.set_menu(menu)
 
   Gtk.main()

```

---

### Post by r-senior on 2012-03-12
I think there are probably another couple of things worth thinking about with regard to this threaded implementation:

1. Synchronization of that global status variable. Or the lack of it. ;) Have a look at the locking mechanisms in threading, e.g. Lock.

[http://docs.python.org/library/threading.html#lock-objects](http://docs.python.org/library/threading.html#lock-objects)

Even things like your print statements might need to have a lock around them if you don't want a garbled log. (But maybe they are only temporary).

2. GUI updates - you have multiple threads updating the GUI. You'd be better off asking the GUI's run loop to do the updates when it is idle, rather than doing the updates direct. It's easy to do - bundle your GUI updates into a method and ask the main thread to do them when it falls idle:

```
GObject.idle_add(my_gui_update_method)
```

The GUI updates outside the run() methods should be OK.

---

