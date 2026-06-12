---
title: "pyGtk treeview problem"
date: 2008-02-08
forum: Programming Talk
---

### Post by piratenaapje on 2008-02-08
I'm trying to use a treeview to display info about some files, but the problem is, some file names are VERY long, and the treeview will display the full name
What I'm trying to figure out is how to be able to select the place in between the columns, drag, and make the column width larger or smaller, like I can do with a pane

Is there any way to do this with pygtk?

```
#!/usr/bin/python

import os
import glob
import sys
import stat
try:
	import pygtk
	pygtk.require("2.0")
except:
	sys.exit('pygtk 2.0 or higher is required')
try:
	import gtk
	import gtk.glade
except:
	sys.exit('gtk and gtk.glade are required')

class TreeView:

	# close the window and quit
	def delete_event(self, widget, event, data=None):
		gtk.main_quit()
		return False
	
	def get_main_menu(self, window):
		accel_group = gtk.AccelGroup()
		item_factory = gtk.ItemFactory(gtk.MenuBar, "<main>", accel_group)

		# This method generates the menu items. Pass to the item factory
		#  the list of menu items
		item_factory.create_items(self.menu_items)

		# Attach the new accelerator group to the window.
		window.add_accel_group(accel_group)

		# need to keep a reference to item_factory to prevent its destruction
		self.item_factory = item_factory
		# Finally, return the actual menu bar created by the item factory.
		return item_factory.get_widget("<main>")
	
	def selectCategory(self, selection):
		return selection[0] + 1
	

	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("VcViewer")
		self.window.set_size_request (800, 600)
		self.liststore = gtk.ListStore(str, str)
		self.window.connect("delete_event", self.delete_event)
		self.window.sm = gtk.TreeModelSort(self.liststore)
		self.window.tv = gtk.TreeView(self.window.sm)
		
		self.window.vbox = gtk.VBox()
		self.window.add (self.window.vbox)
		self.window.hpane = gtk.HPaned()
		
		self.window.sw = gtk.ScrolledWindow()
		self.window.sw.add(self.window.tv)
		self.window.toolbar = gtk.Toolbar()
		self.window.toolbar.set_orientation(gtk.ORIENTATION_HORIZONTAL)
		self.window.toolbar.set_style(gtk.TOOLBAR_BOTH)
		self.window.toolbar.set_border_width(5)
		self.window.sw.set_size_request(600, -1)
		self.window.hpane.add(self.window.sw)
		
		self.menu_items = (
			( "/_File",         None,         None, 0, "<Branch>" ),
			( "/File/_New",     "<control>N", None, 0, None ),
			( "/File/_Open",    "<control>O", None, 0, None ),
			( "/File/_Save",    "<control>S", None, 0, None ),
			( "/File/Save _As", None,         None, 0, None ),
			( "/File/sep1",     None,         None, 0, "<Separator>" ),
			( "/File/Quit",     "<control>Q", gtk.main_quit, 0, None ),
			( "/_Options",      None,         None, 0, "<Branch>" ),
			( "/Options/Toffe _Opties",  None,         None, 0, None ),
			( "/_Help",         None,         None, 0, "<Branch>" ),
			( "/_Help/About",   None,         None, 0, None )
		)
		
		self.window.menubar = self.get_main_menu(self.window)	
		self.window.vbox.pack_start(self.window.menubar, False, True, 0)
		
		iconw = gtk.Image() # icon widget
		iconw.set_from_file("gtk.xpm")
		icon_button = self.window.toolbar.append_element(
			gtk.TOOLBAR_CHILD_RADIOBUTTON, # type of element
			None,                          # widget
			"Icon",                        # label
			"Only icons in toolbar",       # tooltip
			"Private",                     # tooltip private string
			iconw,                         # icon
			None,
			self)                       # data for signal
		self.icon_button = icon_button
		
		
		self.window.vbox.pack_start (self.window.toolbar, expand=False, fill=False, padding=0)
		self.window.vbox.pack_start (self.window.hpane)
		
		self.window.table = gtk.Table(2, 4, False)
		self.window.hpane.add (self.window.table)
		
		self.window.tv.column = [None]*4
		self.window.tv.column[0] = gtk.TreeViewColumn('Title')
		self.window.tv.column[1] = gtk.TreeViewColumn('Year')
		self.window.tv.column[2] = gtk.TreeViewColumn('Summary')
		self.window.tv.column[3] = gtk.TreeViewColumn('Extra info')
		self.window.tv.cell = [None]*4
		for i in range(4):
			self.window.tv.cell[i] = gtk.CellRendererText()		
			self.window.tv.column[i].set_sort_column_id(i)			
			self.window.tv.column[i].set_expand(False)
			self.window.tv.append_column(self.window.tv.column[i])
			self.window.tv.column[i].pack_start(self.window.tv.cell[i], True)
			self.window.tv.column[i].set_attributes(self.window.tv.cell[i], text=i)
		self.window.show_all()
		test = self.window.sm.get_model().append(['a very long item in the list, I want to show it less of this item :(, come on, you can do it treeview!', 'didn\'t work, what a bummer'])

def main():
	gtk.main()

if __name__ == "__main__":
	tvexample = TreeView()
	main()
```

---

### Post by Majorix on 2008-02-08
Looking at the screenie, can't you resize the columns? There should also be options like sorting etc, built in. If not, try a different toolkit like python-wxgtk or tk.

---

### Post by piratenaapje on 2008-02-08
The columns are sortable, I just can't change their width for some reason

---

### Post by Quikee on 2008-02-09
[PHP]for i in range(4):
			self.window.tv.cell[i] = gtk.CellRendererText()		
			self.window.tv.column[i].set_sort_column_id(i)			
			self.window.tv.column[i].set_expand(False)
			self.window.tv.append_column(self.window.tv.column[i])
			self.window.tv.column[i].pack_start(self.window.tv.cell[i], True)
			self.window.tv.column[i].set_attributes(self.window.tv.cell[i], text=i)
[/PHP]

Just add here: 
[PHP]self.window.tv.column[i].set_resizable(True)[/PHP]
to make columns resizable.

---

### Post by piratenaapje on 2008-02-09
Thanks! It works now ;)

---

### Post by NoBugs! on 2010-02-11
That works, but the column is always initially set as wide as the longest cell. What if you want the column to be resizable for the user, _and_ have a certain default width when data is added to it? From what I've seen it seems you can't do this in gtk, I haven't found a simple set-current-width command...

---

### Post by NoBugs! on 2010-02-11
It looks like this fixes it:
```

		col.set_fixed_width(100)
		col.set_sizing(gtk.TREE_VIEW_COLUMN_FIXED)
		col.set_resizable(True)
		col.set_reorderable(True)

```
I had sizing set to auto.

---

