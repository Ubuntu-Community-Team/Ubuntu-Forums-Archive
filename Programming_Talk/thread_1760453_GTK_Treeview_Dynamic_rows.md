---
title: "GTK Treeview Dynamic rows"
date: 2011-05-16
forum: Programming Talk
---

### Post by hapyfishrmn on 2011-05-16
Hello all,
 I am new to gtk and have used the tutorials available, but I seem to hit a wall. I am trying to add rows dynamically to a gtk tree view. The tree shows with the proper column headings, but no data.

Here is how I set up the tree view
```

GtkWidget *trv_Registry;
GtkListStore *str_Registry;
GtkTreeViewColumn  *col;

    //TreeView(trv_Registry)
    trv_Registry = gtk_tree_view_new();
    gtk_container_add(GTK_CONTAINER(scl_List), 
                      trv_Registry);
    str_Registry = gtk_list_store_new(4,
                                      G_TYPE_STRING,   //First
                                      G_TYPE_STRING,   //Last
                                      G_TYPE_STRING,   //City
                                      G_TYPE_STRING);  //State
    gtk_tree_view_set_model(GTK_TREE_VIEW(trv_Registry), 
                            GTK_TREE_MODEL(str_Registry));

    //First
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "First");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //Last
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "Last");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //City
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "City");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //State
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "State");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);   
    gtk_widget_show(trv_Registry);

```

Here is my function that is supposed to dynamically add rows from the GTK entries, but nothing gets added.

```

void AddTreeEntry()
{
GtkTreeIter    iter;
GtkListStore  *liststore;

liststore = gtk_list_store_new(4,
                               G_TYPE_STRING,
                               G_TYPE_STRING,
                               G_TYPE_STRING,
                               G_TYPE_STRING);


    gtk_list_store_append(GTK_LIST_STORE(liststore), 
                          &iter);
    gtk_list_store_set(GTK_LIST_STORE(liststore), 
                       &iter,
                       0, 
                       gtk_entry_get_text(GTK_ENTRY(ent_First)), 
                       1,
                       gtk_entry_get_text(GTK_ENTRY(ent_Last)),
                       2,
                       gtk_entry_get_text(GTK_ENTRY(ent_City)), 
                       3,
                       gtk_entry_get_text(GTK_ENTRY(ent_State)),
                       -1);                                            //indicates the end

    gtk_tree_view_set_model(GTK_TREE_VIEW(trv_Registry), 
                            GTK_TREE_MODEL(liststore));

    g_object_unref(liststore);
    return;
}

```

---

### Post by JupiterV2 on 2011-05-17
First off, in your function which creates the TreeView, you do not need to retain a reference to the TreeStore. Instead, you should g_object_unref your local reference, otherwise you'll have a memory leak. The TreeView creates its own reference to the store for you.

```
store = gtk_tree_store_new (...);
gtk_tree_view_set_model (..., GTK_TREE_MODEL(store));
g_object_unref (store);
```

In your second function, you simply need to get the model from your treeview and append new entries to it. You don't create a new store.
```
GtkModel *model = gtk_tree_view_get_model (treeview);
gtk_list_store_append(GTK_LIST_STORE(model), &iter, NULL);
gtk_list_store_set(GTK_LIST_STORE(model), &iter, ...);
```

If, however, you are planning on doing a LOT of insertions (1000+) at once, it is recommended you actually unref the old model and create a new one. This is because the treeview is automatically updated with each change to the referenced model.

```
GtkListStore *new_model;
gtk_tree_view_set_model(treeview, NULL); /* unrefs the old model */
gtk_list_store_new (...);
/* append and store your 1000+ rows of data */
gtk_tree_view_set_model(treeview, new_model);
g_object_unref (new_model);

```

I hope this helps!

---

### Post by hapyfishrmn on 2011-05-17
1.My row gets added but no data is in the row. Is the data hidden? I can select a row but no visible data.

2.If I do single entries that could go over 1000 should I use your third code snippet or does that apply only when your doing 1000+ at once?

I reduced my code down to a minimal example
Thanks for your help
```


#include <gtk/gtk.h>
GtkWidget           *win_Main;
GtkWidget           *scl_List;
GtkWidget           *tbl_Main;
GtkListStore        *str_Registry;
GtkWidget           *trv_Registry;
GtkWidget           *btn_key_Add;
GtkTreeViewColumn   *col;

//---------------------------------------------------------
// AddTreeEntry
//---------------------------------------------------------
void AddTreeEntry()
{
GtkTreeIter    iter;
GtkTreeModel *model;

    model = gtk_tree_view_get_model(GTK_TREE_VIEW(trv_Registry));
    gtk_list_store_append(GTK_LIST_STORE(model), 
                          &iter);
    gtk_list_store_set(GTK_LIST_STORE(model), 
                       &iter,
                       0, 
                       "John", 
                       1,
                       "Doe",
                       2,
                       "Somewhere", 
                       3,
                       "KS",
                       -1);                                            //indicates the end
    gtk_tree_view_set_model(GTK_TREE_VIEW(trv_Registry), 
                            model);
    return;
}

int main (int argc, char **argv)
{
    gtk_init (&argc, &argv);

int                  NumColumns = 4;

    //Window(win_Main)
    win_Main = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title(GTK_WINDOW(win_Main),             //Casting window to set title
                                    "GTK app");
    g_signal_connect(win_Main,                             //widget responding to event
                        "delete_event",                       //
                        gtk_main_quit,                        //kill window is programmer named
                        NULL);    

    //Table(tbl_Main)
    tbl_Main = gtk_table_new(2, 1, FALSE);
    gtk_widget_show(tbl_Main);
    gtk_container_add(GTK_CONTAINER(win_Main), tbl_Main);

    //ScrollWindow(scl_List)
    scl_List = gtk_scrolled_window_new(NULL, 
                                       NULL);
    gtk_scrolled_window_set_policy(GTK_SCROLLED_WINDOW(scl_List),
                                   GTK_POLICY_NEVER,
                                   GTK_POLICY_ALWAYS);
    gtk_table_attach(GTK_TABLE(tbl_Main), 
                      scl_List, 
                       0, 1, 0, 1,
                     (GtkAttachOptions)(GTK_EXPAND | GTK_FILL),
                     (GtkAttachOptions)(GTK_EXPAND | GTK_FILL), 0, 0);
    gtk_widget_show(scl_List);

    //TreeView(trv_Registry)
    trv_Registry = gtk_tree_view_new();
    trv_Registry->name = "trv_Registry";
    gtk_container_add(GTK_CONTAINER(scl_List), 
                      trv_Registry);
    str_Registry = gtk_list_store_new(4,
                                      G_TYPE_STRING,   //First
                                      G_TYPE_STRING,   //Last
                                      G_TYPE_STRING,   //City
                                      G_TYPE_STRING);  //State
    gtk_tree_view_set_model(GTK_TREE_VIEW(trv_Registry), 
                            GTK_TREE_MODEL(str_Registry));

    g_object_unref(str_Registry);
    //First
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "First");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //Last
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "Last");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //City
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "City");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);
    //State
    col = gtk_tree_view_column_new();
    gtk_tree_view_column_set_title(col, "State");   
    gtk_tree_view_append_column(GTK_TREE_VIEW(trv_Registry), col);   
    gtk_widget_show(trv_Registry);

    //Button(btn_key_Add)
    btn_key_Add = gtk_button_new_with_label("Add");
    gtk_widget_show(btn_key_Add);
    gtk_table_attach(GTK_TABLE(tbl_Main), 
                     btn_key_Add, 
                     0, 1, 2, 3,
                    (GtkAttachOptions)(GTK_FILL),
                    (GtkAttachOptions)(GTK_FILL), 0, 2);
    g_signal_connect(btn_key_Add, 
                     "clicked",
                     G_CALLBACK(AddTreeEntry),
                     NULL);

  gtk_widget_show_all (win_Main);

  gtk_main ();

  return 0;
}


```

---

### Post by SledgeHammer_999 on 2011-05-18
I use the C++ API not the C API but I think I know where your problem is.

You have to remeber this: **TreeView** columns are different from the **TreeModel** columns. Each TreeView column **can** have **multiple** TreeModel columns associated with it.

In your code I see that you create the TreeView columns but you don't associate any TreeModel column with them.

I am not sure how you do this with the C API though. Maybe this tutorial has the answer-> [http://scentric.net/tutorial/treeview-tutorial.html](http://scentric.net/tutorial/treeview-tutorial.html)

---

### Post by JupiterV2 on 2011-05-18
Yes, my third snippet is only used when inserting 1000+ rows all at once.

As for why the data is not being displayed:

You need to specify a cell renderer which will actually display the data for your rows/columns and you need to tell each column what data it will represent. The order of the data in TreeModel doesn't have to directly correspond to the order of your TreeViewColumns.

[PHP]GtkCellRenderer *renderer = gtk_cell_renderer_text_new ();
GtkTreeViewColumn *column = gtk_tree_view_column_new_with_atrributes (
"Title",                 /* a title for the column */
renderer,                /* the renderer you're using to represent the data */
"text", TEXT_COLUMN,     /* tell the column which data its displaying */
...,                     /* additional attributes, if required */
NULL);[/PHP]

I highly recommend using an enumerator to specify what each column represents. It makes life a lot easier:

```
enum MyColumns {
    COLUMN_SOMETEXT,
    COLUMN_OTHERTEXT,
    COLUMN_SOMEDATA,
    N_COLUMNS
};
```

Also see: [http://developer.gnome.org/gtk/stable/]("http://developer.gnome.org/gtk/stable/")

[EDIT]I should also add that the above enumerator help clarify the following code:
```
gtk_list_store_set(GTK_LIST_STORE(model), 
                       &iter,
                       COLUMN_FIRSTNAME, 
                       "John", 
                       COLUMN_LASTNAME,
                       "Doe",
                       COLUMN_CITY,
                       "Somewhere", 
                       COLUMN_STATE,
                       "KS",
                       -1);
``` [/EDIT]

---

### Post by hapyfishrmn on 2011-05-20
@JupiterV2
 I dont mean to be an idiot, I have been reading tutorials and using your suggestions and I get a row but the data goes in outside of the already created columns. If I' trying to add a row why do I create a new column?  I'm starting with the column headings already defined, so I dont want to add new attributes. Really confused.

So here is my sequence, this I think adds the data to the list store, but doesn't display it in the tree view:
 1. gtk_tree_view_get_model()
 2. gtk_tree_view_get_model()
 3. gtk_list_store_set()
 4. gtk_tree_view_set_model() 
 5. gtk_tree_view_set_model()
 6. g_object_unref

To display in the tree view, I use the cell renderer:
 7. gtk_tree_view_column_new
 8. gtk_cell_renderer_text_new
 9. gtk_tree_view_column_pack_start
 10. g_object_set
 11. gtk_tree_view_append_column

---

### Post by JupiterV2 on 2011-05-21
The key to understanding TreeViews in Gtk+ is that the interface, the TreeView itself, is completely independent of the data, the TreeModel.

Creating the "view":

1. Create the TreeView.
2. Select and create a renderer for the data you want to represent.
3. Create a column and attach the renderer to it.
4. Repeat steps 2 and 3 until you've got all the columns you need.

Creating the "data":
1. Create a TreeModel (List or Store).
2. Attach the model to the TreeView.

The point to all this is to reinforce that the data is independent of the view. This allows you to attach different models to the same view on the fly. Or, more importantly, you can use multiple views to represent a single data model. This is most useful when you want each view to display different parts of the same model.

```

enum StoreColumns {
  COL_ONE,
  COL_TWO,
  N_COL
};

GtkTreeIter iter;
GtkTreeStore *store = NULL;
GtkTreeView *treeview = NULL;
GtkCellRenderer *renderer = NULL;

/* create the data model */
gtk_tree_store_new (N_COL, 
  G_TYPE_STRING,
  G_TYPE_INT);

gtk_tree_store_append (store, &iter, NULL);
gtk_tree_store_set (store, &iter,
  COL_ONE, "sometext",
  COL_TWO, 1,
  -1);

/* create the 'view' to display the data */
treeview = gtk_tree_view_new_with_model (model);
g_object_unref (model); /* reference no longer needed */

renderer = gtk_cell_renderer_text_new ();
column = gtk_tree_view_column_new_with_attributes (
  "Text Column", renderer,
  "text", COL_ONE,
  NULL);
gtk_tree_view_append_column (GTK_TREE_VIEW (treeview), column);

```

That, in a nutshell, are the steps you need to take to build a very basic treeview. Note the separation between the code storing the data and the code creating the viewable content. When adding new rows to your data, you need only get the model from the treeview and add data to it. Three function calls would suffice:
```
GtkTreeModel *model;
GtkTreeIter iter;

model = gtk_tree_view_get_model (GTK_TREE_VIEW (treeview);
gtk_tree_store_append (GTK_TREE_STORE (model), &iter, NULL);
gtk_tree_store_set (GTK_TREE_STORE (model), &iter,
  COL_ONE, "moretext",
  -1);

```

That's all you'll need. GTK+ will take care of displaying the data automatically.

Does this help clarify some confusion?

---

### Post by hapyfishrmn on 2011-05-22
@JupiterV2,
Finally I understand, whew! Thanks for your persistence & patience.
For me understanding that the store and a model are the same thing, helped as well. Here is my basic code that works for those who are trying the same thing. I was not understanding the sequence of events properly. Thanks again, you were a big help.

```


#include <gtk/gtk.h>
GtkWidget           *win_Main;
GtkWidget           *scl_List;
GtkWidget           *tbl_Main;

GtkTreeIter         iter;
GtkTreeStore        *store = NULL;
GtkWidget           *treeview = NULL;
GtkCellRenderer     *renderer = NULL;
GtkTreeStore *model;

GtkWidget           *btn_key_Add;
GtkTreeViewColumn   *col;

enum StoreColumns {
  COL_ONE,
  COL_TWO,
  N_COL
};
//---------------------------------------------------------
// AddTreeEntry
//---------------------------------------------------------
void AddTreeEntry()
{

GtkTreeModel *model;
GtkTreeIter iter;

    model = gtk_tree_view_get_model (GTK_TREE_VIEW (treeview));
    gtk_tree_store_append (GTK_TREE_STORE (model), &iter, NULL);
    gtk_tree_store_set (GTK_TREE_STORE (model), &iter,
                          COL_ONE, "John",
                          COL_TWO, "Doe",
                          -1);
    return;
}

int main (int argc, char **argv)
{
    gtk_init (&argc, &argv);

int  NumColumns = 2;

    //Window(win_Main)
    win_Main = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title(GTK_WINDOW(win_Main),             //Casting window to set title
                                    "GTK app");
    g_signal_connect(win_Main,                             //widget responding to event
                        "delete_event",                       //
                        gtk_main_quit,                        //kill window is programmer named
                        NULL);    

    //Table(tbl_Main)
    tbl_Main = gtk_table_new(2, 1, FALSE);
    gtk_widget_show(tbl_Main);
    gtk_container_add(GTK_CONTAINER(win_Main), tbl_Main);

    //ScrollWindow(scl_List)
    scl_List = gtk_scrolled_window_new(NULL, 
                                       NULL);
    gtk_scrolled_window_set_policy(GTK_SCROLLED_WINDOW(scl_List),
                                   GTK_POLICY_NEVER,
                                   GTK_POLICY_ALWAYS);
    gtk_table_attach(GTK_TABLE(tbl_Main), 
                      scl_List, 
                       0, 1, 0, 1,
                     (GtkAttachOptions)(GTK_EXPAND | GTK_FILL),
                     (GtkAttachOptions)(GTK_EXPAND | GTK_FILL), 0, 0);
    gtk_widget_show(scl_List);

    //TreeView(treeview)
    /* create the data model */
    model = gtk_tree_store_new(N_COL, 
                               G_TYPE_STRING,
                               G_TYPE_STRING);
    treeview = gtk_tree_view_new_with_model(GTK_TREE_MODEL(model));
    g_object_unref(model);

    renderer = gtk_cell_renderer_text_new ();
    col = gtk_tree_view_column_new_with_attributes("First", 
                                                   renderer,
                                                   "text", COL_ONE,
                                                   NULL);
    gtk_tree_view_append_column(GTK_TREE_VIEW(treeview),
                                col);
    col = gtk_tree_view_column_new_with_attributes("Last", 
                                                   renderer,
                                                   "text", COL_TWO,
                                                   NULL);
    gtk_tree_view_append_column(GTK_TREE_VIEW(treeview),
                                col);
    gtk_container_add(GTK_CONTAINER(scl_List), 
                      GTK_WIDGET(treeview));

    //Button(btn_key_Add)
    btn_key_Add = gtk_button_new_with_label("Add");
    gtk_widget_show(btn_key_Add);
    gtk_table_attach(GTK_TABLE(tbl_Main), 
                     btn_key_Add, 
                     0, 1, 2, 3,
                    (GtkAttachOptions)(GTK_FILL),
                    (GtkAttachOptions)(GTK_FILL), 0, 2);
    g_signal_connect(btn_key_Add, 
                     "clicked",
                     G_CALLBACK(AddTreeEntry),
                     NULL);

  gtk_widget_show_all (win_Main);

  gtk_main ();

  return 0;
}


```

---

