---
title: "PyGTK: Drag and Drop Files"
date: 2011-09-05
forum: Programming Talk
---

### Post by _winnetou_ on 2011-09-05
Hello,

id like to start dragging files on my app..
so i created __drag_data_get_data(self, treeview, context, selection, target_id,etime) function. How can i pass into the selection the list of files i want to drag.
And second, is enabling drag and drop by
self.__browser.drag_source_set(gtk.gdk.BUTTON1_MASK,
                               [( 'text/uri-list', 0, 80)],
                               gtk.gdk.ACTION_DEFAULT)
the correct way, meaning is 'text/uri-list' the correct type. Because e.g. nautilus does not respond to that type.

Thanks!
Bye,
Philipp

---

