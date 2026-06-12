---
title: "PyGTK Toolbar - Shows As A Dropdown?"
date: 2008-04-14
forum: Programming Talk
---

### Post by Doppelganger319 on 2008-04-14
[FONT="Verdana"][SIZE="3"]

Fellow programmers,

I am starting out with PyGTK and am trying to implement a simple toolbar with custom icons. I had a perfect toolbar until I decided to eliminate the deprecated warnings. Such methods as append_item() have been deprecated in later versions of Python. The only one that is supported seems to be insert(). When I used this method instead, it transformed my entire menu into a dropdown one, which is not what I want.

Could anyone help me out? I would greatly appreciate. My code is seen below.
[/SIZE][/FONT]

[PHP]#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class Browser:
    # This method is connected to the Close button or
    # closing the window from the WM
    def close_window(self, widget, event=None):
        gtk.main_quit()
        return False

    def make_toolbar_button(self, file_name, label, tooltip, handler):
	iconw = gtk.Image()
	iconw.set_from_file(file_name)
	tb_item = gtk.ToolButton(iconw, label)
	tb_item.set_tooltip_text(tooltip)
	tb_item.connect('clicked', handler)
	tb_item.show()
	return tb_item

    def make_toolbar_entry(self, label, length, handler):
	entry = gtk.Entry()
	tb_item = gtk.ToolItem()
	tb_item.add(entry)
	entry.connect('activate', handler)
        entry.set_width_chars(length)
	entry.set_text(label)
	entry.show()
	return tb_item

    def make_toolbar(self):
        # Create a new hbox with the appropriate homogeneous
        # and spacing settings
        	
	toolbar = gtk.Toolbar()
        toolbar.set_orientation(gtk.ORIENTATION_HORIZONTAL)
        toolbar.set_style(gtk.TOOLBAR_BOTH)
        toolbar.set_border_width(1)
	        
        # Insert Back, Forward, Report, Compare, and Search Buttons
	toolbar.insert(self.make_toolbar_button("./Images/Arrow-Right.png", 
		       "Back", "Go Back One Page", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/Arrow-Left.png", 
		       "Forward", "Go Forward One Page", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/documents3.png", 
		       "Report", "", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/Rename.png", 
		       "Compare", "", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/Find.png", 
		       "Search", "Perform An Advanced Search", self.close_window), 0)

	# Insert Search Entry Box
	toolbar.insert(self.make_toolbar_entry("Type your simple search query here", 50, self.close_window), 0)


	# Insert OK, Settings, Help, and Close Buttons
	toolbar.insert(self.make_toolbar_button("./Images/Symbol-Check.png", 
		       "OK", "Confirm Simple Search Query", self.close_window), 0)
        toolbar.insert(self.make_toolbar_button("./Images/Config-Tools.png", 
		       "Settings", "Configure This Application", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/Help.png", 
		       "Help", "Get Help On This Application", self.close_window), 0)
	toolbar.insert(self.make_toolbar_button("./Images/Symbol-Delete.png", 
		       "Quit", "Quit This Application", self.close_window), 0)
      
        return toolbar;

    def make_tree_structure(self):

	sw = gtk.ScrolledWindow()
	sw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)

	# create a TreeStore with one string column to use as the model
        treestore = gtk.TreeStore(str)

        # we'll add some data now - 4 rows with 3 child rows each
        for parent in range(20):
            piter = treestore.append(None, ['parent %i' % parent])
            for child in range(3):
                treestore.append(piter, ['child %i of parent %i' %
                                              (child, parent)])

        # create the TreeView using treestore
        treeview = gtk.TreeView(treestore)

        # create the TreeViewColumn to display the data
        tvcolumn = gtk.TreeViewColumn('Hierarchy')

        # add tvcolumn to treeview
        treeview.append_column(tvcolumn)

        # create a CellRendererText to render the data
        cell = gtk.CellRendererText()

        # add the cell to the tvcolumn and allow it to expand
        tvcolumn.pack_start(cell, True)

        # set the cell "text" attribute to column 0 - retrieve text
        # from that column in treestore
        tvcolumn.add_attribute(cell, 'text', 0)

        # make it searchable
        treeview.set_search_column(0)

        # Allow sorting on the column
        tvcolumn.set_sort_column_id(0)

        # Allow drag and drop reordering of rows
        treeview.set_reorderable(True)
	
	# Alternate colors for every row
	treeview.set_rules_hint(True)

	sw.add(treeview)
	sw.show()
	treeview.show()

	return sw


    def make_text_pane(self):
	
	# create scrolled window
	sw = gtk.ScrolledWindow()
        sw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)

	# create text view and add to scrolled window
        textview = gtk.TextView()
        textbuffer = textview.get_buffer()
        sw.add(textview)
        sw.show()
        textview.show()

	return sw

    
    # even easier, just check given toggle button and enable/disable 
    # tooltips
    def toggle_event(self, widget, toolbar):
        toolbar.set_tooltips(widget.get_active())

    def __init__(self):
        # Here is our main window (a dialog) and a handle for the handlebox
        # Ok, we need a toolbar, an icon with a mask (one for all of 
        # the buttons) and an icon widget to put this icon in (but 
        # we'll create a separate widget for each button)
        # create a new window with a given title, and nice size

	window = gtk.Window(gtk.WINDOW_TOPLEVEL)
	window.set_title("Browser")      # add the version number
        window.set_size_request(1130, 860)
        window.set_resizable(False)

	window.connect("delete_event", self.close_window)

	fixed = gtk.Fixed()
	window.add(fixed)
	fixed.show()

	menu = self.make_toolbar()
	fixed.put(menu, 0, 0)
	menu.show()

	fixed.put(gtk.HSeparator(), 0, 64)

	hpaned = gtk.HPaned()
	hpaned.set_size_request(1130, 730)
	hpaned.set_position(367)
	fixed.put(hpaned, 0, 64)
        hpaned.show()

        # Now create the contents of the two halves of the window
	tree_structure = self.make_tree_structure()
        hpaned.add1(tree_structure)
        #tree_structure.show()

        text_pane = self.make_text_pane()
        hpaned.add2(text_pane)
	text_pane.show()

	status_bar = gtk.Statusbar()
	fixed.put(status_bar, 0, 795)
	status_bar.show()	
	
	cid = status_bar.get_context_id("oid")
	status_bar.push(cid, "The status bar displays the OID of the selected object")
	status_bar.set_has_resize_grip(False)
	

	window.show()

def main():
    # rest in gtk_main and wait for the fun to begin!
    gtk.main()
    return 0

if __name__ == "__main__":
    Browser()
    main()[/PHP]

---

### Post by tseliot on 2008-04-15
I have edited your post. Next time you should put your code using either CODE tags (see the "#" icon) or PHP tags so that indentation is kept and that the code doesn't take too much space.

---

### Post by Doppelganger319 on 2008-04-15
I have a different approach to the question:

Is there an example of creating a PyGTK toolbar that includes buttons with custom images and a text entry using only the insert() method of gtk.Toolbar()?

If someone has sample code, that would be perfect.

---

