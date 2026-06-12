---
title: "PyGtk signal order"
date: 2008-10-08
forum: Programming Talk
---

### Post by mike_g on 2008-10-08
I have two events each firing a signal which calls a function.

Event A is called when a text_view loses focus and updates the text in an object.

Event B is called when a row in a tree_view is selected and sets the content of the text_view to the value stored in the object. 

My problem is that if I am focused on the text_view and click on the tree_view event B runs first causing the object text to be set to the wrong value.

I want event A to run first. How can I do this? 

Heres an extract of the code I am using in case its of any help:
```

		self.content_store = gtk.TreeStore(str, object)
		self.content_view = gtk.TreeView(self.content_store)
		self.content_view.set_model(self.content_store)
		self.content_view.connect("cursor_changed", self.content_select)

...

		self.text_view = gtk.TextView()
		self.text_view.connect("focus_out_event", self.update_text)

...

	""" WHEN TEXT FIELD LOSES FOCUS UPDATE LINKED OBJECT TEXT """
	def update_text(self, widget, data=None):
		print "Text Lost Focus"
		model, row = self.content_view.get_selection().get_selected()
		if not row: return 		
		label = self.content_store.get_value(row, 0)
		entry = self.content_store.get_value(row, 1)
		""" GRAB CONTENT OF TEXT BUFFER """
		textbuffer = self.text_view.get_buffer()
		startiter, enditer = textbuffer.get_bounds()
		text = textbuffer.get_text(startiter, enditer)
		entry.text = text
		self.content_store.set_value(row, 0, text)	

...

	def content_select(self, data=None):
		print "Content Select"	
		model, row = self.content_view.get_selection().get_selected()
		entry = self.content_store.get_value(row, 1)
		self.text_view.get_buffer().set_text(entry.text)
```

---

