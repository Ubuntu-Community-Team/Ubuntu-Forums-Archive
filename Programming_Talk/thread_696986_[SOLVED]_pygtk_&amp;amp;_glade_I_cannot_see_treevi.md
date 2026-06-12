---
title: "[SOLVED] pygtk &amp;amp; glade I cannot see treeview"
date: 2008-02-14
forum: Programming Talk
---

### Post by quintok on 2008-02-14
hi guys. I'm having a problem that I think is either caused by the treeview not getting repainted or my glade file is incorrect and is hiding the treeview so that I cannot see it being updated.

This method is called after a button is pressed and after some data collection is done to fill QC.DVDs and QC.DVDs[i].Titles.

[PHP]
self.tvDVDs = self.tvDVDs = self.wTree.get_widget("tvDVDs")
self.treeStore = gtk.TreeStore(str)
[/PHP]

[PHP]
   def UpdateTree(self):
      for dvd in self.QC.DVDs:
         # At least 1 dvd
         iter = self.treeStore.append(None, [dvd.DiscTitle])
         for title in dvd.Titles:
            self.treeStore.append(iter, [title.DescribeTitle()])
      self.tvDVDs = gtk.TreeView(self.treeStore)
      self.tvColumn = gtk.TreeViewColumn('DVDs')
      self.tvDVDs.append_column(self.tvColumn)
      self.cell = gtk.CellRendererText()
      self.tvColumn.pack_start(self.cell, True)
      self.tvColumn.add_attribute(self.cell, 'text', 0)
      print "Tree Updated"
[/PHP]

I'm attatched the .glade file incase it is that instead

---

### Post by slavik on 2008-02-14
did you link the treestore to the treeview? (I am not a pygtk expert but I don't see anything resembling a linking call).

I think you can to call the set_model() method of the treeview with the reference of the treestore.

---

### Post by quintok on 2008-02-14
I believe this line does this:
[PHP]self.tvDVDs = gtk.TreeView(self.treeStore)[/PHP]
However after your comment I did try set_model() specifically of self.tvDVDs passing self.treeStore and that appeared to not change anything.

---

### Post by quintok on 2008-02-14
bah, as expected a stupid mistake.  I was refering to "tvDVDs" in the script when it was "tvDvds" in the glade file.  Thank you for looking anyway

---

