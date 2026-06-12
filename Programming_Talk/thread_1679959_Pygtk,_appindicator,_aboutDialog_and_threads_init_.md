---
title: "Pygtk, appindicator, aboutDialog and threads_init problem"
date: 2011-02-01
forum: Programming Talk
---

### Post by snakerdlk on 2011-02-01
Hi,
I'm having a problem implementing the following:
This creates a tray icon with canonicals appindicator with two options, about and quit. When pressing about it should open a new window, created by gtk.aboutDialog().

It does open the window but when I close it, the app freezes.

```

#!/usr/bin/python

import sys
import gobject
import gtk
import appindicator

def destroy(widget, event=None):
	print "destroyed"
	sys.exit(0)

def about(widget, event=None):
	aboutdialog = gtk.AboutDialog()
			
	aboutdialog.set_name("Test")
	aboutdialog.set_version("1.0")
	
	aboutdialog.run()

	aboutdialog.destroy()
	
if __name__ == "__main__":
	ind = appindicator.Indicator ("example-simple-client",
			"indicator-messages",
			appindicator.CATEGORY_APPLICATION_STATUS)
	ind.set_status (appindicator.STATUS_ACTIVE)
	ind.set_attention_icon ("new-messages-red")
  	# create a menu
   	menu = gtk.Menu()

	about_item = gtk.MenuItem("About")
	about_item.connect("activate", about, "status clicked")
	about_item.show()
	menu.append(about_item)

	quit_item = gtk.MenuItem("Quit")
	quit_item.connect("activate", destroy, "file.quit")
	quit_item.show()
	menu.append(quit_item)

  	ind.set_menu(menu)
  	
  	gtk.gdk.threads_init()

    	gtk.main()

```

The same code implemented just with pygtk does not have the same error:
```

#!/usr/bin/python

import sys
import gobject
import gtk
import appindicator

def destroy(widget, event=None):
	print "destroyed"
	sys.exit(0)

def about(widget, event=None):
	aboutdialog = gtk.AboutDialog()
			
	aboutdialog.set_name("Test")
	aboutdialog.set_version("1.0")
	
	aboutdialog.run()

	aboutdialog.destroy()
	
class trayIcon(gtk.StatusIcon):
		def __init__(self):
			gtk.StatusIcon.__init__(self)
			
			self.set_from_stock(gtk.STOCK_FIND)
			self.set_tooltip('Tracker Desktop Search')
			self.set_visible(True)

			self.menu = menu = gtk.Menu()

			about_item = gtk.MenuItem("About")
			about_item.connect("activate", about,"about")
			menu.append(about_item)

			quit_item = gtk.MenuItem("Quit")
			quit_item.connect("activate", self.destroy_button, "file.quit")
			menu.append(quit_item)
			menu.show_all()

			self.connect('popup-menu', self.icon_clicked)

		def icon_clicked(self, status, button, time):
			self.menu.popup(None, None, None, button, time)

		def destroy_button(self,widget,event=None):
			sys.exit(0)
	
if __name__ == "__main__":
	trayIcon()
  	
  	gtk.gdk.threads_init()

    	gtk.main()

```

How do I fix this? Apparently a but in appindicator...
I've tested with eggtrayicon, which is very similar to the code implemented only with pygtk, and it works too.

If it IS a bug, where do I report it ?
Or where should I look for help?

Thanks

---

