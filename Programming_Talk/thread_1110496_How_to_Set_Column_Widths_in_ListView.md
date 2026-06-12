---
title: "How to Set Column Widths in ListView?"
date: 2009-03-29
forum: Programming Talk
---

### Post by rich1939 on 2009-03-29
I have a treeview that contains 4 text columns and I have installed column headers for them. The first two columns are the width of the column header text, but I want the 3rd column to be fairly wide to hold a long description that might be wrapped onto multiple lines. The 4th column can be normal width. Here's the code I've written for the 3rd column:

```

    renderer = gtk_cell_renderer_text_new();
    g_object_set(G_OBJECT(renderer), "editable", TRUE, "editable-set", TRUE, "width-chars", 80,
        "wrap-mode", PANGO_WRAP_WORD, "wrap-width", 78, NULL);
    g_signal_connect(G_OBJECT(renderer), "edited", G_CALLBACK(description_edited),
        (gpointer) tmTreeview);
    column = gtk_tree_view_column_new_with_attributes("Task Description Entry", renderer,
        "text", DESCRIPTION, NULL);
    gtk_tree_view_append_column(GTK_TREE_VIEW(tmTreeview), column);

```

For some reason, no matter what properties I set for the column, it remains only the width of the header text, and then the 4th column occupies the remainder of the window's width.

Any idea what I'm doing wrong?

---

