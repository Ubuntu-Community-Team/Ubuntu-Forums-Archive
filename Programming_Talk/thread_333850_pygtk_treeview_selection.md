---
title: "pygtk treeview selection?"
date: 2007-01-08
forum: Programming Talk
---

### Post by Cirdan7 on 2007-01-08
What is the best way to get the selected item in a TreeView and get the most out of it. I got it to work where something happens if you click on the item, but when you click it, the selected item doesn't get highlighted. Also, how to I get the actually text of a selected item?

```
#!/usr/bin/env python
################
##
## Ubuntu Control Panel
## Version 0.3
## One main interface for editing settings in Ubuntu
## Uses gnome applications
##
#################


import os
import pygtk
pygtk.require('2.0')
import gtk, gobject

class mainWindow:
	def __init__(self):
		"""Initialization"""

		# Create lists
		self.categories = [ "Display", "Hardware", "Multimedia", "Networking" ]
		
				 #Item name: 		command
		self.display = { 'Theme': "gnome-theme-manager",\
				 'Screensaver':	"gnome-screensaver-preferences",\
				 'Resolution': "gnome-display-properties",\
				 'Font': "gnome-font-properties",\
				 'Wallpaper': "gnome-background-properties %F",\
				 'Windows': "gnome-window-properties",\
				 'Session Properties': "gnome-session-properties"}

		self.hardware = { 'Keyboard': 				"gnome-keyboard-properties",\
				  'Keyboard Shortcuts': 		"gnome-keybinding-properties",\
				  'Mouse': 				"gnome-mouse-properties",\
				  'Removeable Drives and Media': 	"gnome-volume-properties"}

		self.multimedia = { 'Sound': 				"gnome-sound-properties"}

		self.networking = { 'Network Preferences': 		"gnome-network-preferences"}


		# Create the window
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Ubuntu Control Panel 0.3")
		self.window.connect("destroy", lambda w : gtk.main_quit())
		self.window.set_size_request(285, 300)
		self.window.set_border_width(10)
		
		self.windowBox = gtk.HBox(False, 0)
		self.window.add(self.windowBox)

		self.leftBox = gtk.VBox(False, 0)
		self.rightBox = gtk.VBox(False, 0)

		self.windowBox.add(self.leftBox)
		self.windowBox.add(self.rightBox)
		
		self.categoryPane = self.createCategoryList()
		self.toolPane = self.createToolList(self.display)

		self.leftBox.pack_start(self.categoryPane)
		self.rightBox.pack_start(self.toolPane)

		# ow the window and widgets
		self.leftBox.show()
		self.rightBox.show()
		self.categoryPane.show()
		self.toolPane.show()
		self.windowBox.show()
		self.window.show()
	
	def main(self):
		gtk.main()

	def createCategoryList(self):
		"""Create the Category list view"""
		scroll_window = gtk.ScrolledWindow()

		scroll_window.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
		model = gtk.ListStore(gobject.TYPE_STRING)
		tree_view = gtk.TreeView(model)
		scroll_window.add_with_viewport(tree_view)
		tree_view.show()
		
		for each in self.categories:
			model.set(model.append(), 0, each)

		tree_selection = tree_view.get_selection()
		tree_selection.set_mode(gtk.SELECTION_SINGLE)
		tree_selection.set_select_function(self.selectCategory)

		cell = gtk.CellRendererText()
		column = gtk.TreeViewColumn("Categories", cell, text=0)
		tree_view.append_column(column)

		return scroll_window

	def selectCategory(self, selection):
		print selection				

	def createToolList(self, dic):
		"""Create the Tool list view"""
		scroll_window = gtk.ScrolledWindow()

		scroll_window.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
		model = gtk.ListStore(gobject.TYPE_STRING)
		tree_view = gtk.TreeView(model)
		scroll_window.add_with_viewport(tree_view)
		tree_view.show()
		
		for toolName in dic:
			model.set(model.append(), 0, toolName)

		cell = gtk.CellRendererText()
		column = gtk.TreeViewColumn("Setting", cell, text=0)
		tree_view.append_column(column)

		return scroll_window

	def runTool(self, dic, name):
		#runTool(self.display, "Theme")
		pid = os.fork()
		if pid:
			os.system(dic[name])
	
def main():
	window = mainWindow()
	window.main()


if __name__ == "__main__":
	main()


```

---

### Post by pretto on 2007-03-29
The problem is that your selectCategory function

must return True as  under:

def selectCategory(self, selection):
        print selection
        return True                

read more here [http://www.pygtk.org/docs/pygtk/class-gtktreeselection.html#method-gtktreeselection--set-select-function](http://www.pygtk.org/docs/pygtk/class-gtktreeselection.html#method-gtktreeselection--set-select-function)

---

