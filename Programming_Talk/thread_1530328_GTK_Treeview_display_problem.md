---
title: "GTK Treeview display problem"
date: 2010-07-13
forum: Programming Talk
---

### Post by xefix on 2010-07-13
I am trying to display some data in a new window with a TreeView when a button is clicked. Within Glade, I've created a treeview with a single column, a cellrenderer for text, and a datastore model. I am now trying to add text to the column. In addition to the function that shows the window containing TreeView (which seems to be working fine as the window showsup without errors), here's the function that gets called when the button is clicked (it is indeed called - I've stepped through it with gdb):

```

void
refreshList(){
	GtkTreeModel *datastore;
	GtkTreeIter iter;
	char *text = "Test text";
	datastore = gtk_tree_view_get_model(tree);
	gtk_list_store_append(GTK_LIST_STORE(datastore), &iter);
	gtk_list_store_set(GTK_LIST_STORE(datastore), &iter, 0, text, -1);
}

```

tree is the pointer to the treeview, I initialized it as a global variable:

```
GtkTreeView *tree = NULL;
```

and got the pointer to it in my main function:
```
tree = GTK_TREE_VIEW(gtk_builder_get_object(builder, "treeview"));
```


When I compile the program (with no errors), start it and click on the button, I see the window with the treeview pop up, but the column is empty. There are no errors, and when I stepped through the code, both iter and datastore contained some data, though I don't really know how to check whether what they had was correct. Maybe I'm not using the right functions? Can any people knowledgeable about GTK point me in the right direction?

---

### Post by PaulM1985 on 2010-07-13
This may help you:

[http://scentric.net/tutorial/treeview-tutorial.html](http://scentric.net/tutorial/treeview-tutorial.html)

Paul

---

### Post by xefix on 2010-07-13
I've actually read a lot of that tutorial and based some of my code on it, but it doesn't have an explanation on TreeView that was created in Glade.

---

### Post by xefix on 2010-07-13
Got it! I just needed to set the text property of the cell renderer to the column number (0) in Glade, and everything now shows up!

---

