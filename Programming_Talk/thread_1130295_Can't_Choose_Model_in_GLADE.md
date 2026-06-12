---
title: "Can't Choose Model in GLADE"
date: 2009-04-19
forum: Programming Talk
---

### Post by rich1939 on 2009-04-19
I have designed a GtkTreeView in GLADE 3 and in the General Options, it asks for "TreeView Model:" and has a button to click that opens a dialog that supposedly offers a choice of models. The contents of the dialog are empty here.

I'm getting runtime errors when the (converted) Glade file is read, as follows:

```

    builder = gtk_builder_new();
    gtk_builder_add_from_file(builder, "myprog.xml", NULL);

```

The error messages are as follows:

```

(myprog:16337): Gtk-CRITICAL **: gtk_tree_row_reference_new: assertion 'GTK_IS_TREE_MODEL (model)' failed

(myprog:16337): Gtk-CRITICAL **: gtk_cell_view_set_displayed_row: assertion 'GTK_IS_TREE_MODEL (cell_view->priv->model)' failed

```

I'm thinking that Glade should present me with a list of models, including the GtkTreeModel and GtkListStore that I want to use.

Is this a bug is Glade 3?

BTH: The program runs properly in Debug mode, but crashes with these same errors in Release mode.

---

