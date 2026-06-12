---
title: "TreeView issues in GTK with Python"
date: 2006-12-12
forum: Programming Talk
---

### Post by sethmahoney on 2006-12-12
Okay, here's the deal: I've got a TreeView set up with two columns, with toggles in the left column and text in the right.  Everything looks fineish, but the toggles won't toggle (and I went and set the 'activatable' property to True and everything!  Any thoughts?  Here's the code:

```
		#load in the XML data files
		self.fields_list = xml_attribs_list("fieldlist.xml")
		self.tags_list = xml_attribs_list("taglist.xml")
		#get my glade file
		self.gladefile = "pyCites.glade"
		self.gladetree = gtk.glade.XML(self.gladefile, "cite_window")
		#get all the widgets I need
		self.window = self.gladetree.get_widget("cite_window")
		self.fields_list_view = self.gladetree.get_widget("fields_list_view")
		#add fields to the fields_list_view
		self.fields_liststore = gtk.ListStore(gobject.TYPE_BOOLEAN, gobject.TYPE_STRING)
		self.setup_liststore()
		#set up columns for the fields_list_view
		self.fields_list_view_column_toggle = gtk.TreeViewColumn("")
		self.fields_list_view.append_column(self.fields_list_view_column_toggle)
		self.fields_list_view_column_text = gtk.TreeViewColumn("Field")
		self.fields_list_view.append_column(self.fields_list_view_column_text)
		#set up cell renderers for the fields_list_view and connect them to columns
		self.fields_list_view_cell_renderer_toggle = gtk.CellRendererToggle()
		self.fields_list_view_cell_renderer_toggle.set_property('activatable', True)
		self.fields_list_view_column_toggle.pack_end(self.fields_list_view_cell_renderer_toggle, True)
		self.fields_list_view_cell_renderer_text = gtk.CellRendererText()
		self.fields_list_view_column_text.pack_end(self.fields_list_view_cell_renderer_text, True)
		self.fields_list_view_column_text.add_attribute(self.fields_list_view_cell_renderer_text, "text", 1)
		self.fields_list_view.set_model(self.fields_liststore)
		print(self.fields_list_view_cell_renderer_toggle.get_property('activatable'))
		#set up callbacks for the fields_list_view
		self.fields_list_view_cell_renderer_toggle.connect("toggled", self.fields_list_view_cell_renderer_toggle_cb, (self.fields_liststore, self.fields_list_view_column_toggle))
		#show the window!
		self.window.show()
```

---

### Post by sethmahoney on 2006-12-13
Nevermind, got it to work - apparently the callback function has to explicitely set the toggle state using set_active()

---

