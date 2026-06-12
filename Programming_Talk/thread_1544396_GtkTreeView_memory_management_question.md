---
title: "GtkTreeView memory management question"
date: 2010-08-02
forum: Programming Talk
---

### Post by tylerburtonca on 2010-08-02
Hi,

I have searched all over the net for anything that could answer this question for me but I haven't had any luck yet. I was hoping that you fine people here could give me a hand.

Let me preface this by saying that while I know some C I am very new to Linux (and especially Gtk) development. I have followed some tutorials but can't seem to nail down where a memory leak is coming from. I have two functions addRow and clearRows as defined below:

/* adds a row of dummy data filling each column element with a string */
void addRow{
	//create an iter to add data from
	GtkTreeIter iter;
	//The TreeView store
	GtkListStore *store = NULL;

	//grab a copy of the existing store (if one exists)
	store = (GtkListStore *)gtk_tree_view_get_model((GtkTreeView *)myTreeView);

	if(store == NULL)
	{
		//create a GType array for the number of columns we want
		GType *types = g_new0(GType, numCols);

		//set all of the types to string
		for(int i=0; i<numCols; i++)
			types[i] = G_TYPE_STRING;

		//create a new store of the above types
		store = gtk_list_store_newv(numCols,types);

		//free the memory used by the GTypes
		free(types);
	}else
		g_object_ref(store);

	//configure the iter to append to the model
	gtk_list_store_append(store, &iter);

	//loop through the array and populate the columns
	for(int i=0; i<numCols;i++)
	{
		gtk_list_store_set(store, &iter,i,"dummy data",-1);
	}

	//set the model of the treeview to display the new data
	gtk_tree_view_set_model(GTK_TREE_VIEW(myTreeView),GTK_TREE_MODEL(store));

        //free my reference
	g_object_unref(store);
}

/* get rid of all rows from the tree view */
void clearRows{

	//grab a copy of the existing store (if one exists)
	GtkListStore *store = (GtkListStore *)gtk_tree_view_get_model((GtkTreeView *)myTreeView);

	if(store != NULL)
	{
		gtk_list_store_clear(store);
	}
}

When I run the above functions in a loop like this

/* test adding 1,000 rows and then removing them to see if we leak memory */
void testAddAndRemove{
	for(int i=0;i<1000;i++)
		addRow();

	clearRows();
}

my memory increases but is never released. I must be missing something simple. Could anyone suggest a fix or clue me in on where my problem is?

Thanks a lot!

---

