---
title: "Gtkmm sorcery"
date: 2009-02-23
forum: Programming Talk
---

### Post by cl333r on 2009-02-23
Hi folks,
I found out that both
```
Gtk::TreeView::Column *pColumn=m_TreeView.get_column(cols_count-1);
```
and
```
Gtk::TreeViewColumn *pColumn=m_TreeView.get_column(cols_count-1);
```
compile and execute well.
Does anyone know of a link where I can read about why one can write both Gtk::TreeView::Column and Gtk::TreeViewColumn with same success?

---

### Post by cabalas on 2009-02-23
Not as much sorcery as you might think, the second is just a typedef of the first, it mentions it somewhere in the docs.

On the chance you haven't run across typedef before [http://en.wikipedia.org/wiki/Typedef](http://en.wikipedia.org/wiki/Typedef)

---

### Post by cl333r on 2009-02-23
thanks

---

