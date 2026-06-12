---
title: "Segmentation fault"
date: 2011-03-23
forum: Programming Talk
---

### Post by qw3rty_rocks on 2011-03-23
I keep getting this error in gtk+

Here is the code, can someone see whats wrong?

```
//Includes:

#include <gtk/gtk.h>
#include <string>
using namespace std;

string APPLIST[10];

void getApps()
{
	GDir *dir;
	dir = g_dir_open( "./apps", 0, NULL );
	string filename = "";
	int i = 0;
	while((filename = g_dir_read_name(dir)) != "")
	{
		APPLIST[i] = filename;
		i++;
	}
	g_dir_close(dir);
	
	// build app list
	return;
}

/*static GtkWidget *
create_list_view (void)
{
	GtkCellRenderer    *renderer;
	GtkTreeViewColumn  *col;
	GtkTreeSelection   *sel;
	GtkListStore       *liststore;
	GtkWidget          *view;

	liststore = gtk_list_store_new(NUM_COLS, G_TYPE_STRING); // NUM_COLS = 1 

	view = gtk_tree_view_new_with_model(GTK_TREE_MODEL(liststore));

	renderer = gtk_cell_renderer_text_new();
	col = gtk_tree_view_column_new();

	gtk_tree_view_column_pack_start(col, renderer, TRUE);
  gtk_tree_view_column_add_attribute(col, renderer, "text", COL_TEXT);
	gtk_tree_view_column_set_title(col, " Your items here ");

	gtk_tree_view_append_column(GTK_TREE_VIEW(view), col);

	sel = gtk_tree_view_get_selection(GTK_TREE_VIEW(view));
	gtk_tree_selection_set_mode(sel, GTK_SELECTION_SINGLE);
	g_signal_connect(sel, "changed", G_CALLBACK(onSelectionChanged), liststore);

	return view;
}*/

//Close button event

void on_window_destroy (GtkObject *object, gpointer user_data)
{
	gtk_main_quit();
}

int main( int   argc,
          char *argv[] )
{
    //Declare variables
    
    GtkWidget *window;
    GtkWidget *libraryButton;
    GtkWidget *storeButton;
    GtkWidget *optionsButton;
    GtkWidget *pageHolder;
    GtkWidget *tabLabel;
    
    GtkWidget *LibraryHbox;
    
    GtkWidget *libraryGamesList;
    
    //Initialise gtk
    
    gtk_init (&argc, &argv);
    
    //Setup the window
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_default_size(GTK_WINDOW(window), 640, 480);
    gtk_container_border_width (GTK_CONTAINER (window), 10);
    
    //Setup tabs/pages
    
    pageHolder = gtk_notebook_new ();
    gtk_notebook_set_tab_pos (GTK_NOTEBOOK (pageHolder), GTK_POS_LEFT);
    
    //Setup library
    
    LibraryHbox = gtk_hbox_new(FALSE, 0);
    tabLabel = gtk_label_new ("Library");
    gtk_label_set_angle(GTK_LABEL(tabLabel),90);
    gtk_notebook_append_page(GTK_NOTEBOOK (pageHolder), LibraryHbox, tabLabel);
    
    getApps();
    
    /*libraryGamesList  = create_list_view();
    gtk_container_add (GTK_CONTAINER (LibraryHbox), libraryGamesList);*/
    
    //Setup store
    
    storeButton = gtk_button_new_with_label ("Store");
    tabLabel = gtk_label_new ("Store");
    gtk_label_set_angle(GTK_LABEL(tabLabel),90);
    gtk_notebook_append_page(GTK_NOTEBOOK (pageHolder), storeButton, tabLabel);
    gtk_container_add (GTK_CONTAINER (window), pageHolder);
    
    //Setup options
    
    optionsButton = gtk_button_new_with_label ("Options");
    tabLabel = gtk_label_new ("Options");
    gtk_label_set_angle(GTK_LABEL(tabLabel),90);
    gtk_notebook_append_page(GTK_NOTEBOOK (pageHolder), optionsButton, tabLabel);
    gtk_container_add (GTK_CONTAINER (window), pageHolder);
    
    //Show all objects
    
    gtk_widget_show_all (window);
    
    //Main loop
    
    gtk_main ();
    
    return 0;
}
```

---

### Post by Some Penguin on 2011-03-23
Have you put any effort into debugging at all?  I don't see where you've bothered to show a stack trace or even a line number, for instance.

You're also populating APPLIST although you're not using it; you're not doing any checking whether you're going past the end of the array there; and you didn't bother to check what g_dir_read_name() returns when there aren't any files left, but are instead assuming that it's equivalent to the empty string.

---

### Post by qw3rty_rocks on 2011-03-23
I fixed it all up. :p

---

