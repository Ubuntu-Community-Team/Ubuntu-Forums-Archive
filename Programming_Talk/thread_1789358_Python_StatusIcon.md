---
title: "Python StatusIcon"
date: 2011-06-23
forum: Programming Talk
---

### Post by Hairy_Palms on 2011-06-23
hi all, im trying to get a statusicon right click menu to work in pygobject the icon appears fine and no errors are output, however no menu appears, the problem line i think is
```
menu.popup(None, None, None, Gtk.StatusIcon.position_menu, button, time)
```

the old working code in pygtk was

```
menu.popup(None, None, gtk.status_icon_position_menu, button, time, self.statusicon)
```

this is the complete example code.

```
from gi.repository import Gtk

class StatusIcon:
    def __init__(self):
        self.statusicon = Gtk.StatusIcon()
        self.statusicon.set_from_stock(Gtk.STOCK_HOME) 
        self.statusicon.connect("popup-menu", self.right_click_event)
        
        window = Gtk.Window()
        window.connect("destroy", lambda w: Gtk.main_quit())
        window.show_all()
		
    def right_click_event(self, icon, button, time):
        menu = Gtk.Menu()

        about = Gtk.MenuItem()
	about.set_label("About")
        quit = Gtk.MenuItem()
	quit.set_label("Quit")
        
        about.connect("activate", self.show_about_dialog)
        quit.connect("activate", Gtk.main_quit)
        
        menu.append(about)
        menu.append(quit)
        
        menu.show_all()

        #menu.popup(None, None, gtk.status_icon_position_menu, button, time, self.statusicon)
        menu.popup(None, None, None, Gtk.StatusIcon.position_menu, button, time)
        
    def show_about_dialog(self, widget):
        about_dialog = Gtk.AboutDialog()

        about_dialog.set_destroy_with_parent(True)
        about_dialog.set_name("StatusIcon Example")
        about_dialog.set_version("1.0")
        about_dialog.set_authors(["Andrew Steele"])
        		
        about_dialog.run()
        about_dialog.destroy()

StatusIcon()
Gtk.main()
```

anyone got any ideas what im doing wrong?

---

### Post by Hairy_Palms on 2011-06-24
bump

---

### Post by Hairy_Palms on 2011-06-27
if anyone else has this problem, youve got to keep your menu in scope or it gets garbage collected, so you get no errors but no menu either, this is the working code

```
from gi.repository import Gtk

class aStatusIcon:
    def __init__(self):
        self.statusicon = Gtk.StatusIcon()
        self.statusicon.set_from_stock(Gtk.STOCK_HOME) 
        self.statusicon.connect("popup-menu", self.right_click_event)

        window = Gtk.Window()
        window.connect("destroy", lambda w: Gtk.main_quit())
        window.show_all()

    def right_click_event(self, icon, button, time):
        self.menu = Gtk.Menu()

        about = Gtk.MenuItem()
    about.set_label("About")
        quit = Gtk.MenuItem()
    quit.set_label("Quit")

        about.connect("activate", self.show_about_dialog)
        quit.connect("activate", Gtk.main_quit)

        self.menu.append(about)
        self.menu.append(quit)

        self.menu.show_all()

    def pos(menu, ignore, icon):
        return (Gtk.StatusIcon.position_menu(menu, icon))

        self.menu.popup(None, None, pos, self.statusicon, button, time) 

    def show_about_dialog(self, widget):
        about_dialog = Gtk.AboutDialog()

        about_dialog.set_destroy_with_parent(True)
        about_dialog.set_name("StatusIcon Example")
        about_dialog.set_version("1.0")
        about_dialog.set_authors(["Andrew Steele"])

        about_dialog.run()
        about_dialog.destroy()

aStatusIcon()
Gtk.main()
```

---

