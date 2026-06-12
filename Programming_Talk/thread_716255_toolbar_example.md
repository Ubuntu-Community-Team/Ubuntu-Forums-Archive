---
title: "toolbar example"
date: 2008-03-05
forum: Programming Talk
---

### Post by Tony37 on 2008-03-05
I tried the following toolbar example:
[http://www.pygtk.org/pygtk2tutorial/examples/toolbar.py](http://www.pygtk.org/pygtk2tutorial/examples/toolbar.py)

While the example ran, it reported a long series of warning: deprecated. One was for insert_space.

I looked this up and found it should be insert(item,pos) where item is a gtk.ToolItem. 

I looked up gtk.ToolItem. However, I could find nothing which explains what items are ToolItems (e.g. space?). I tried a lot of googles without luck in finding any tutorial, examples, ... which shows building a toolbar with the 'insert'.

Sadly, there does not appear to be any text comparable to GTK+ Development which focuses on pygtk.

Can anyone point me to trustworthy current sources on how to implement pygtk guis?

Thanks,

Tony

---

### Post by Can+~ on 2008-03-05
Instead of using the pygtk tutorial, use the reference directly once you dominate gtk, since the tutorial is a bit deprecated.

[http://www.pygtk.org/pygtk2reference/class-gtktoolitem.html](http://www.pygtk.org/pygtk2reference/class-gtktoolitem.html)

Also, consider using python + gtk.glade for easy interfaces, taking out the burden of packing everything.

---

### Post by Tony37 on 2008-03-31
Further experimentation revealed that a ToolItem is a container and that the desired widget needs to be added to the toolitem and the toolitem inserted in the toolbar, e.g.

        self.file_entry = gtk.Entry()
        dummy = gtk.ToolItem()
        dummy.add(self.file_entry)
        self.file_entry.connect('activate', self.file_entry_activated)
        file_toolbar.insert(dummy, -1)
        self.file_entry.set_text('new.txt')
        self.file_entry.show()

---

