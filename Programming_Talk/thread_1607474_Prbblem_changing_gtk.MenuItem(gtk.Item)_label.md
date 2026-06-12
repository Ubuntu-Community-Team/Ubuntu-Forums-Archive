---
title: "Prbblem changing gtk.MenuItem(gtk.Item) label"
date: 2010-10-27
forum: Programming Talk
---

### Post by snakerdlk on 2010-10-27
Hi,

consider the code:
```

#!/usr/bin/python

import sys
import gobject
import gtk
import appindicator

def status_clicked(widget, event=None):
	global ind
	global status_item
	print "status_clicked:",event
	if ind.get_status() == appindicator.STATUS_ACTIVE:
		ind.set_status(appindicator.STATUS_ATTENTION)
		status_item.get_child().set_label("Change To Act")
	else:
		ind.set_status(appindicator.STATUS_ACTIVE)
		status_item.get_child().set_label("Change To Att")
	print "new label:", status_item.get_child().get_label()

def destroy(widget, event=None):
	print "destroyed"
	sys.exit(0)

if __name__ == "__main__":
	ind = appindicator.Indicator ("example-simple-client",
			"indicator-messages",
			appindicator.CATEGORY_APPLICATION_STATUS)
	ind.set_status (appindicator.STATUS_ACTIVE)
	ind.set_attention_icon ("new-messages-red")
  	# create a menu
   	menu = gtk.Menu()

	status_item = gtk.MenuItem("test")
	status_item.connect("activate", status_clicked, "status clicked")
	status_item.show()
	menu.append(status_item)

	quit_item = gtk.MenuItem("Quit")
	quit_item.connect("activate", destroy, "file.quit")
	quit_item.show()
	menu.append(quit_item)

	status_item.get_child().set_label("Change To Att")

  	ind.set_menu(menu)

    	gtk.main()

```

before the ```
ind.set_menu(menu)
``` the ```
status_item.get_child().set_label("Change To Att")
``` changes the label.

But the handle ```
status_clicked
``` changes the label but isnt updated in the menu.

I tried with status_item.[show(),show_now(),show_all(),map(),realize(),...] but nothing.

What am I doing wrong?
Thanks

---

### Post by snakerdlk on 2010-10-29
bump

---

