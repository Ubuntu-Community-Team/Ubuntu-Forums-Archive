---
title: "PyGTK TreeView. How to reset TreeViewColumn width?"
date: 2010-01-20
forum: Programming Talk
---

### Post by frpaul on 2010-01-20
Hi. I made a simple file browser. When user changes directory, programm clears TreeModel and loads new data into it. How to reset width of the 1st column according to the length of filenames in the new directory. Its important when filenames are shorter, than in the previous directory and a lot of extra space between the columns is left.

---

### Post by steeleyuk on 2010-01-20
I believe you can use one of three options... gtk.TREE_VIEW_COLUMN_GROW_ONLY, gtk.TREE_VIEW_COLUMN_AUTOSIZE or gtk.TREE_VIEW_COLUMN_FIXED.

```
column.set_sizing(gtk.TREE_VIEW_COLUMN_AUTOSIZE)
```

I've not tested it though so no guarantees on it being what you need.

---

### Post by frpaul on 2010-01-21
> **steeleyuk said:**
> I believe you can use one of three options... gtk.TREE_VIEW_COLUMN_GROW_ONLY, gtk.TREE_VIEW_COLUMN_AUTOSIZE or gtk.TREE_VIEW_COLUMN_FIXED.

```
column.set_sizing(gtk.TREE_VIEW_COLUMN_AUTOSIZE)
```I've not tested it though so no guarantees on it being what you need.

Thanks! I'll check it out.

---

