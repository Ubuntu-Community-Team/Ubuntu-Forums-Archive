---
title: "[SOLVED] python error: got multiple values for keyword argument"
date: 2008-12-31
forum: Programming Talk
---

### Post by giuspen on 2008-12-31
I can't understand the error: 
TypeError: open_file_dialog() got multiple values for keyword argument 'filter_pattern'

the error is at the following line:

[PHP]filepath = self.open_file_dialog(self, filter_pattern='*.py', filter_name='Python Source Files')[/PHP]

while the function is:

[PHP]	def open_file_dialog(self, filter_pattern=None, filter_name=None):
		"""The application's open file dialog, returns the retrieved filepath"""
		chooser = gtk.FileChooserDialog(	parent=self.window,
													flags=gtk.DIALOG_MODAL|gtk.DIALOG_DESTROY_WITH_PARENT,
													action=gtk.FILE_CHOOSER_ACTION_OPEN,
													buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_OK) )
		
		if filter_pattern != None:
			filter = gtk.FileFilter()
			filter.set_name(filter_name)
			filter.add_pattern(filter_pattern)
			chooser.add_filter(filter)
		if chooser.run() == gtk.RESPONSE_OK:
			filepath = chooser.get_filename()
			chooser.destroy()
			return filepath
		else:
			chooser.destroy()
			return None[/PHP]

thanks to anybody takes a look.

---

### Post by Tony Flury on 2008-12-31
> **giuspen said:**
> 
the error is at the following line:

[PHP]filepath = self.open_file_dialog(self, filter_pattern='*.py', filter_name='Python Source Files')[/PHP]


You don't need to pass self as an argument when you are calling a class method - it gets passed automatically.

The reason you get the error is that the method sees the "self" value that you pass as an unamed argument - which it then thinks is a filter_pattern

What you need to call is 

[PHP]filepath = self.open_file_dialog(filter_pattern='*.py', filter_name='Python Source Files')[/PHP]

Your method definition is correct - don't change that

---

