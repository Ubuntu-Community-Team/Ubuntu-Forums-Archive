---
title: "Nautilus python"
date: 2010-09-25
forum: Programming Talk
---

### Post by Asafe on 2010-09-25
I'm a python noob and wrote the following code for a nautilus extension:
```
#!/usr/local/bin/python
# -*- coding: utf-8 -*-

import urllib
import gtk
import pygtk
import nautilus
import gconf 
import gtk.glade

class Slide (nautilus.MenuProvider):	
	f = None
	def __init__(self):
		self.client = gconf.client_get_default() 			
		self.f = gtk.glade.XML( "papel.glade" ) 
		self.window = self.f.get_widget("window1")		
		gtk.main()

	def oi (self):				        		
		self.window.show()
			
	def menu_activate_cb(self, menu, file):
		self.oi()
				
	def get_file_items(self, window,files):
		if len(files) != 1:
			return
	    	item = nautilus.MenuItem('NautilusPython::slide_file_item','Slide','Slide')
	        item.connect('activate', self.menu_activate_cb, files[0])
		return item,

	def get_background_items(self, window, file):
	 	item = nautilus.MenuItem('NautilusPython::slide_item','Slide','Slide')
	 	item.connect('activate', self.menu_background_activate_cb, file)
	 	return item, 

	def menu_background_activate_cb(self, menu, file):
		self.oi()


``` 
But it doesn't work. If I comment the lines:
```
self.f = gtk.glade.XML( "papel.glade" ) 
		self.window = self.f.get_widget("window1")		
		gtk.main()
``` the code works but I can't see any problem in those lines. Any help?

---

