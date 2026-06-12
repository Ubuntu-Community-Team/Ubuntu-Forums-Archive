---
title: "[pygtk] Need help with pixbuf's in treeview"
date: 2010-08-11
forum: Programming Talk
---

### Post by The Midnight Coder on 2010-08-11
Hi. I need some help getting pictures to be shown in a treeview row. After some searching I found that the only way to do this is by using Pixbufs. I tried getting it to work but no luck so far :(

Can someone help me. This is the code:

```

		self.liststore = gtk.ListStore(gtk.gdk.Pixbuf, str, str)

		self.treeview = gtk.TreeView(self.liststore)
		self.treeview.set_size_request(20,380)
		self.treeview.set_headers_visible(False)

		self.column = gtk.TreeViewColumn('Pixbuf')
		self.column1 = gtk.TreeViewColumn('Text')
		
		self.img1 = gtk.gdk.pixbuf_new_from_file("file.jpg")

		self.liststore.append([self.img1, True, 'Text'])

		self.treeview.append_column(self.column)
		self.treeview.append_column(self.column1)

		self.cellpb = gtk.CellRendererPixbuf()
		self.cell1 = gtk.CellRendererText()

		self.column.pack_start(self.cellpb, True)
		self.column1.pack_start(self.cell1, True)

		self.column1.set_attributes(self.cell1, text=2)

```

---

### Post by steeleyuk on 2010-08-11
Quick example (change image file names as appropriate):

```
#!/usr/bin/env python

import gtk

window = gtk.Window()

liststore = gtk.ListStore(gtk.gdk.Pixbuf)
for f in ["img1.jpg", "img2.jpg", "img3.jpg"]:
    i = gtk.gdk.pixbuf_new_from_file(f)
    liststore.append([i])

treeview = gtk.TreeView(liststore)
cell = gtk.CellRendererPixbuf()
column = gtk.TreeViewColumn("Pixbuf", cell)
column.add_attribute(cell, "pixbuf", 0)
treeview.append_column(column)

window.connect("destroy", lambda w: gtk.main_quit())

window.add(treeview)
window.show_all()

gtk.main()
```

From the looks of the code you posted, you were missing the attributes method on the pixbuf column.

In most cases, the following steps are required to setup TreeView's (and is often the part that trips people up as they forget one of them, or get them in the wrong order):

[LIST]
[*]Create the model
[*]Create the treeview and attach model
[*]Setup the appropriate cells
[*]Specify and attach the columns to the TreeView
[*]Attach the cells to columns
[*]Specify the column/cell attributes
[/LIST]

---

### Post by The Midnight Coder on 2010-08-24
Wow thanks. That did the trick. I'll keep that list in mind because its simple. I had ended up combining alot of examples I had tried to get the treeview to work but after the headache I went through I won't be doing that again.

---

### Post by durand on 2011-05-29
Thanks steeleyuk, that really helped!

---

