---
title: "GtkTreeView Edit Next Column"
date: 2009-03-31
forum: Programming Talk
---

### Post by rich1939 on 2009-03-31
I have a GtkTreeView that's organized as a list of four columns. I have made each column editable and have connected the "edited" signal to a function that transfers the data from the GtkCellEditable text entry into the model's data store.

If I click on a column's cell, I can enter data and then save it by pressing the Enter or Tab keys. With Tab, I'd really like to automatically move to the next cell, but I can't figure out how to do that.

Since Gtk+ automatically creates a Widget on top of the cell to hold the edited data, and then that widget is disposed when the edited data is transferredd to the model's store, I don't see how to automatically cause the next column to be clicked to activate it...nor do I know how to reference an individual column in the GtkTreeView.

From what I've studied, I can reference a row to select it, but I can't figure out how to select an individual column. This **must** be possible somehow.

Any help would be appreciatedd.

---

