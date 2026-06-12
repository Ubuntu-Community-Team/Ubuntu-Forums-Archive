---
title: "pygtk: Sort multiple columns in TreeModel / TreeView"
date: 2007-01-12
forum: Programming Talk
---

### Post by [h2o] on 2007-01-12
I have a gtk.TreeModel which is connected to a table of type gtk.TreeView.
I want to sort this table according to first one, then a second column.

Example: There are 3 columns [date, amount, description]
I want to order first by date, and then by amount. So that I can easily find the largest/smallest amount for a certain date.

How do I do this? The set_sort_column_id() seem to set only one column.

---

### Post by Daverz on 2007-01-13
You have to set a sort func.  Since this uses a compare function, it can be slow.

[http://pygtk.org/pygtk2tutorial/sec-TreeModelInterface.html#sec-SortingTreeModelRows](http://pygtk.org/pygtk2tutorial/sec-TreeModelInterface.html#sec-SortingTreeModelRows)

[http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq13.043.htp](http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq13.043.htp)

---

