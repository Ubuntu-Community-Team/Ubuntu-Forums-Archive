---
title: "glade-3 python treeview"
date: 2009-02-09
forum: Programming Talk
---

### Post by n0p on 2009-02-09
First of all I apologize for my bad english
I am beginner in writing GUI apps with Glade and python, i am having problem with libglade.. well I know that glade-3 hasn't yet good implementation with gtkbuilder, so python users are saving projects in libglade format, and then we convert it with: gtk-builder-convert, to bring up our xml file in gtkbuilder format. Here is my problem, I need treeview, but treeview can only be used in glade if we are saving our project in gtkbuilder format, but i need to use libglade format because i have to convert it with gtk-builder-conver.. So my question is, how can I insert treeview :S

---

### Post by slavik on 2009-02-09
err, what?!

treeview is a gtk widget ... I am not understand what you are having a problem with. I never had a problem making a .glade file with a treeview inside ...

---

### Post by mike_g on 2009-02-09
Just dump an empty treeview widget into your document. AFAIK you will have to write the code populate it tho. Treeviews require a treestore to hold the data. Heres some code I ripped from an old project of mine, which setup a treeview widget and did some stuff with it. Incase its of any help:
```
	def setup_content_tree(self):
		self.content_store = gtk.TreeStore(str, object)
		self.content_view = gtk.TreeView(self.content_store)
		self.content_view.set_model(self.content_store)
		self.content_view.set_size_request(400, 200)
		self.content_view.connect("cursor_changed", self.content_select)
		self.add_col("Content", 0, self.content_view)

		self.content_scroll = gtk.ScrolledWindow()
		self.content_scroll.set_policy(gtk.POLICY_NEVER, gtk.POLICY_AUTOMATIC)
		self.content_scroll.add(self.content_view)		
		self.table.attach(self.content_scroll, 1, 2, 1, 2)
```

---

### Post by n0p on 2009-02-13
ok, i am begginer in python gtk programming, can you help me more and tell me more specific, how to implement that code in my code :D, here are my files

---

