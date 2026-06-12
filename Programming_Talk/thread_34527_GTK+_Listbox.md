---
title: "GTK+ Listbox"
date: 2005-05-15
forum: Programming Talk
---

### Post by john8675309 on 2005-05-15
I am having some trouble with getting a listbox to enumerate items into it.  Using GTK+ and glade.


(Here is my code)
```

void
on_Chooser_show                        (GtkWidget       *widget,
                                        gpointer         user_data)
{

GtkTreeModel *model;
GtkTreeIter   newrow;


treeview  = lookup_widget(GTK_WIDGET(widget), "lstrdp");
printf("Treeview %s\n",treeview);
printf("View is %s\n",GTK_TREE_VIEW(treeview));

/*model = gtk_tree_view_get_model(GTK_TREE_VIEW(treeview));*/
printf("Treeview %s\n",treeview);

printf("Model %s\n",model);
gtk_list_store_append(GTK_LIST_STORE(treeview), &newrow);
gtk_list_store_set(GTK_LIST_STORE(treeview), &newrow, COL_TEXT, "test", -1);
}

```

I am using glade and when I compile the code it works fine, but when I run the code I get:
```

john@laptop:~/Projects/chooser/src# ./chooser 
Treeview P[

View is P[

Treeview P[

Model  %

(chooser:5270): GLib-GObject-WARNING **: invalid cast from `GtkTreeView' to `GtkListStore'

(chooser:5270): Gtk-CRITICAL **: gtk_list_store_append: assertion `GTK_IS_LIST_STORE (list_store)' failed

(chooser:5270): GLib-GObject-WARNING **: invalid cast from `GtkTreeView' to `GtkListStore'

(chooser:5270): Gtk-CRITICAL **: gtk_list_store_set: assertion `GTK_IS_LIST_STORE (list_store)' failed


```

How can I make the list work in callbacks.c?

Thanks,

--John

---

