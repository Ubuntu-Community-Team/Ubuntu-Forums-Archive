---
title: "VALID_ITER error for GtkListStore selection"
date: 2010-01-29
forum: Programming Talk
---

### Post by Milliways on 2010-01-29
I want to change the value of one field of the currently selected row in a view of a GtkListStore

The following code produces an error:-
Gtk-CRITICAL **: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed

```
    selection = gtk_tree_view_get_selection(view);
    if(gtk_tree_selection_get_selected(selection, &model, &iter))
    {
	gtk_list_store_set(liststore, &iter, COL_TAG, TRUE, -1);
    }
```
NOTE The iter is valid, because I can use it to get values with gtk_tree_model_get()

If I convert the iter to a path, then back to an iter it works:-
```
    selection = gtk_tree_view_get_selection(view);
    if(gtk_tree_selection_get_selected(selection, &model, &iter))
    {
	path = gtk_tree_model_get_path(model, &iter);
	gtk_tree_model_get_iter(GTK_TREE_MODEL(liststore), &iter2, path);
	gtk_tree_path_free (path);

	gtk_list_store_set(liststore, &iter2, COL_TAG, TRUE, -1);
    }
```
Can anyone explain why the first code does not work?
Is this a GTK error, or do I not understand?

---

### Post by Milliways on 2010-01-30
I have some more insight into the reason for the failure.
The view is based on a GtkTreeModelFilter, so I guess the iter is pointing to this, rather than the underlying model (but I still think this is a bug).

A related issue, to get the GtkListStore from the model, obtained with gtk_tree_view_get_model(view) I need to do the following:-

```
GtkListStore *liststore =
GTK_LIST_STORE(gtk_tree_model_filter_get_model(GTK_TREE_MODEL_FILTER(model)));
```

---

### Post by Linteg on 2010-02-01
It is a bit complex, true, but GtkTreeModelFilter is just a GtkTreeModel which wraps around another GtkTreeModel to enable filtering. The filter is the underlying model for the GtkTreeView, hence all operations which return references to the underlying model return references to the filter. In order to convert from the filter's iter to one for the underlying model use [gtk_tree_model_filter_convert_iter_to_child_iter]("http://library.gnome.org/devel/gtk/unstable/GtkTreeModelFilter.html#gtk-tree-model-filter-convert-iter-to-child-iter").

---

### Post by Milliways on 2010-02-02
Thanks,
I have included
gtk_tree_model_filter_convert_iter_to_child_iter()
in my code, and this makes things clearer.

---

