---
title: "GtkTreeView Set Model Problem"
date: 2009-04-09
forum: Programming Talk
---

### Post by rich1939 on 2009-04-09
I've created a GtkTreeView with GLADE 3 that I intend to use as a GtkListView. The model is created as follows:

```

GtkListStore *tmStore;

tmStore = gtk_list_store_new(COLUMNS, G_TYPE_STRING, G_TYPE_STRING,
    G_TYPE_STRING, G_TYPE_STRING);

```

I get the GtkTreeView object via GtkBuilder, as follows:

```

tmTreeview = GTK_WIDGET(gtk_builder_get_object(dbBuilder,"tmTimeList"));

```

...and then add the renderers and columns to it.

My problem is the following call:

```

    gtk_tree_view_set_model(GTK_TREE_VIEW(tmTreeview),[COLOR="Red"]GTK_TREE_MODEL(tmStore)[/COLOR]);

```

Because I am using Glade to create the GtkTreeView, I have to add the model after the treeview has been created. But I'm getting a compiler **Warning** concerning the highlighted argument to **gtk_tree_view_set_model**, as follows:

```

[COLOR="Cyan"]/timesheets.c|130|warning: passing argument 2 of ‘gtk_tree_view_set_model’ from incompatible pointer type
[/COLOR]
```

How do I specify the model to GtkTreeView that is being used as a GtkListView?

Any help would be appreciated.

---

### Post by rich1939 on 2009-04-10
Bump

Isn't anyone using GtkTreeView as a ListView? If so, how do you specify the model you're using?

I'm stymied by the warnings (both compile-time and run-time).

---

