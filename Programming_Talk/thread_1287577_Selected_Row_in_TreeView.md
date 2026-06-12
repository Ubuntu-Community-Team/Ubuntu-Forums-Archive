---
title: "Selected Row in TreeView"
date: 2009-10-10
forum: Programming Talk
---

### Post by matmatmat on 2009-10-10
In C# using gtk#, how would you get the selected row in a treeview?

---

### Post by rich1939 on 2009-10-10
> **matmatmat said:**
> In C# using gtk#, how would you get the selected row in a treeview?

I don't know whether C# using gtk# is equivalent to C using gtk+, but if your treeview is a listview using a model containing the view's data, then the following code I wrote might be similar to what you need.

```

    if (gtk_tree_selection_get_selected (selection, &model, &tmIter))
    {
        // Indicate that a selection has been made
        tmSelected = TRUE;
        tmSelection = selection;

        gtk_tree_model_get (model, &tmIter, TM_SERIAL_NO, &tmSERIAL,
            TM_CONTRACT_ID, &contract, TM_ENTRY_DATE, &entry_date,
            TM_DESCRIPTION, &description, TM_TIME_SPENT, &time_spent, -1);

        // store the model's values into the "tmEntries" structure.
        // The structure's fields must be filled so that if the
        // user decides to save a modified copy of the data, all
        // will be available to be stored.

```

Obviously, the TM_SERIAL_NO, TM_CONTRACT_ID, etc., are the enums for the columns in the listview. And, BTW, the routine that contains this code was called via the "tree_selection_changed" signal.

Hope this snippet helps.

-rich-

---

### Post by MadCow108 on 2009-10-10
invoke the get_selection method on the treeview to get a gtk.treeselection. from his you can get the selected row/rows with help of the treemodel
its the same method in gtkmm(c++) and pygtk(python) and I'm guessing also in gtk#(C#)
just check the documentation

---

### Post by matmatmat on 2009-10-11
I have this:
```

tree_3.Selection;

```
which returns a "Gtk.TreeSelection", what do i do with that? I found something on get_selected but it didn't work :confused:

---

### Post by matmatmat on 2009-10-15
bump? anyone?

---

