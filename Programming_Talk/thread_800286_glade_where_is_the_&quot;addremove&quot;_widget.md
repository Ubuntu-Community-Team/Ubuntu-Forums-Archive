---
title: "glade: where is the &quot;add/remove&quot; widget?"
date: 2008-05-19
forum: Programming Talk
---

### Post by days_of_ruin on 2008-05-19
Its used a lot in gnome apps.The one where there is a box with selectable
items that can be removed with the click of the remove button and added with
the add button.But I have no clue how to make one;_;

---

### Post by days_of_ruin on 2008-05-19
Okay I figured out that that is a treeview with the ListStore model.
Thing is glad won't let me edit the treeview model!

---

### Post by slavik on 2008-05-20
treeview model behaves differently based to the storage type you associate with it. (ListStore vs. TreeStore).

---

