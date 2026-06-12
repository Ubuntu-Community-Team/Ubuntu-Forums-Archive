---
title: "GTK Howto: How to Add Tree Views to Windows in C"
date: 2008-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Amit Yaron on 2008-07-23
This guide will teach you how to display tree structures using GTK++. The tree is a useful data structure which consists of nodes. Each node in the tree contains data and pointers to  other nodes, known as their children. A childless node is named leaf. The main node of a tree is named root. 
To each node a path from the root exists.
The Tree View is a component used for displaying data arranged in trees or lists.
I hope this guide will help you understand the concepts of GTK and GLib (a library used by projects such as GTK, GNOME and GIMP).

[SIZE="2"]**1.Downloading GTK++ Headers.**[/SIZE]
To start working developing with Gtk, get libgtk2.0-dev using synaptic or > "sudo apt-get install libgtk-2.0-dev".
&#8207;You will find the header files in the sub-directories of  '/usr/include/gtk-2.0/'.
[SIZE="2"]**2. Downloading GTK Documentation.**[/SIZE]
To start learning GTK, get libgtk2.0-doc using synaptic or > "sudo apt-get install libgtk-2.0-doc".  The tutorial is in the file '/usr/share/doc/libgtk2.0-doc/tutorial/html/book1.html'.
[SIZE="2"]**3.Header Files**[/SIZE]
GTK types are defined in '/usr/include/gtk-2.2/gtk/gtk.h'. When you compile the code you should add the path '/usr/include/gtk-2.2/'. Compiling will be explained later.
In your source, add the following directive:
```
"#include <gtk/gtk.h> "
```
[SIZE="2"]**4.The Main GTK function**[/SIZE]
The main GTK function mcontains:
[LIST=1]
[*]Widget definition.
[*]The command 'gtk_init(argc, argv);
[*]Commands to add widgets and arrange them.
[*]the command 'gtk_main();'.
[/LIST]
The variables 'argc' and 'argv' are command line arguments. To learn more about them type:
```
  "man gtk-options".
```
"argc" is the number of arguments, and "argv" is the list of arguments. the first argument, "argv[0]" is the program name.
The components of a GUI are named Widgets, and their type is "GtkWidget *".
Examples of widgets are: windows, buttons, tree views, horizontal and vertical boxes, etc. The command that adds a widget is 'gtk_<widget type>_new()'. For  example: ```
gtk_window_new().
```
To connect an action with an event (e.g. when user clicks a button), use the command g_signal_connects (object, signal_name, callback_function, user_data). For example:
   ```
 "g_signal_connect (G_OBJECT (window), "destroy", G_CALLBACK (destroy), NULL);
``` ",
 which calls the function 'destroy' when the user clicks the little 'x' that closes the window.
The function destroys receives a widget and the user data as its parameters.

To show the widget use the command```
 gtk_widget_show(widget)
```. It is recommended to display the inner widget prior to the outer one.

The command 'gtk_main()' starts running the GUI application.

[SIZE="2"]**5. Adding the Tree View**[/SIZE]
To create a tree view that can display data we need to define:
[LIST]
[*]An implementation of the Tree Model: 
[LIST]
[*]To display the data in a list structure use a list store.
[*]To display the data in a list structure use a tree store.
[/LIST]A tree model: the tree store or list store, but of type GtkTreeModel.
[*]The tree view. Can be created with a tree model.
[/LIST]
For example:
```
treeStore = gtk_tree_store_new(3, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING); 
```
```
treeModel = GTK_TREE_MODEL(treeStore); 
```

```
treeView = gtk_tree_view_new_with_model(treeModel);
```
Note:
[LIST]
[*]The function 'gtk_tree_store_new' receives a variable list of parameters: the 1st is the number of columns, and the rest are their content types. the variable 'treeStore' is of type GtkTreeStore.
[*]'GTK_TREE_MODEL' is a casting macro. Because C is not object-oriented we need them to convert one type to another type lower or higher in the type hierarchy. To learn more about type hierarchy follow the link: [http://developer.gimp.org/api/2.0/gtk/ch01.html](http://developer.gimp.org/api/2.0/gtk/ch01.html)
[/LIST]

[SIZE="2"]**6 .Adding Data to the Tree**[/SIZE]

[SIZE="2"] _6.1 Adding Columns_[/SIZE]
Each node in the tree is displayed in a row. The content of a node is displayed in columns.
The first step is to insert the columns. The type of a column is 'GtkTreeViewColumn'. You may want to define a renderer for the column first. Well, the type of a renderer is GtkCellRenderer. 
A command to create a renderer may be  ```
'renderer = gtk_cell_renderer_text_new ();'
```
To insert a column use the command:
```
gtk_tree_view_insert_column_with_attributes (GTK_TREE_VIEW (treeView),  
                                                                            position,
                                                                             title,
                                                                             renderer,
                                                                             attributes terminated by NULL);
```
The attributes if the renderer is a text renderer are:
[LIST=1]
[*]the string "text".
[*]the column number, beginning at 0.
[/LIST]
[SIZE="2"]_6.2 Adding a Node (Row)_[/SIZE]
'GtkTreeIter' is the type of iterators or node identifiers.
To Add a row, use one of the following commands:
[LIST]
[*]```
gtk_tree_store_append(treeStore, &newIter, &parent)
```
 	'newIter' and 'parent' are tree iterators. This will add a new node as the last child of 'parent'. The value of 'newIter' will be set to the new node.
[*]```
gtk_tree_store_insert_after (treeStore, &newIter, &parent, &sibling);
```
	'newIter','parent' and 'sibling' are tree iterators. This will add a new node after 'sibling'. If 'sibling' is Null, 'newIter' will be added as the first child. 
[*]```
gtk_tree_store_insert (treeStore, &newIter, &parent, position);
```
	This will add 'newIter' as the child of 'parent' at the position defined by 'position'.
[/LIST]

[SIZE="2"]_6.3 Updating a Cells' Contents_[/SIZE]
To change the contents of cells in the node use the following command:
```
gtk_tree_store_set (treeStore, &iter,
                             column1, value1,
		        column2, value2,
                               .
                               .
                               .
                              column_n, value_n,
                             -1);
```
To learn more about tree store operation, follow the link [http://developer.gimp.org/api/2.0/gtk/GtkTreeStore.html]("http://developer.gimp.org/api/2.0/gtk/GtkTreeStore.html")

[SIZE="2"]_6.4 Editing the Cell_[/SIZE]
To edit the cell you have to make sure the cell is editable:
If the renderer is of type 'GtkCellRenderer' (created by the command gtk_cell_renderer_new), set the value of property 'mode' to GTK_CELL_RENDERER_MODE_EDITABLE.
	The command to set an object's property is ```
'g_object_set(renderer_ptr, property, value, NULL)'.

```          NOTE: All renderers inherit from GtkCellRenderer.
If the renderer is of type 'GtkCellRendererText' (created by the command gtk_cell_renderer_text_new), set the value of property 'editable' to true (1 in C).
	The command to set an object's property is ```
[CODE]'g_object_set(renderer_ptr, property, value, NULL)'.
```[/CODE]
Now, in order for the editing action to take effect, connect the "edited" signal to a callback function using the command:
```
	  
  g_signal_connect(G_OBJECT(renderer),
	           "edited", 
                   G_CALLBACK(editingFunction),
                   user_data);

```
The editing function prototype is:
```
void updateEditedCell (GtkCellRendererText *renderer,

                       gchar               *path,

                       gchar               *new_text,

                       gpointer             user_data);

```To learn more about renderers follow the link:
[http://developer.gimp.org/api/2.0/gtk/GtkCellRenderer.html]("http://developer.gimp.org/api/2.0/gtk/GtkCellRenderer.html")

---

