---
title: "Gtk ScrolledWindows and Adjustments"
date: 2008-04-06
forum: Programming Talk
---

### Post by mike_g on 2008-04-06
I'm having a go at making a colour scheeme generator interface for Gedit. I added a scroll panel to the min window that will hold the various syntax hilighting options. My problem is that I either I don't understnd what the GtkAdjustments do, or I am using them wrong.

According to the [ manual](http://library.gnome.org/devel/gtk/unstable/GtkAdjustment.html) the first three paramaters seem to be: defualt bound, lower bound, and upper bound. 

I presumed that that would be: default panel dimension, minumum panel dimension, maximum panel dimension. But when I run my prog the window allways appears tiny and there is seems to be no limit on how big my scrollpanel will stretch. Changing these vlues dosent seem to make a duifference???

Heres the source (as theres not to much of it yet), The relevant stuff is in the setup_scrollpane function, in main.
```
#include <gtk/gtk.h>
#include <stdlib.h>
#include "constants.h"

typedef struct
{
	GtkWidget *content;
	GtkWidget *name;  // Label holding text about syntax type 
	GtkWidget *fore;  // colour box displaying foreground colour
	GtkWidget *back;  // colour box displaying background colour
	GtkWidget *bold;  // checkbox
	GtkWidget *italic;
	GtkWidget *ulined;
}syntax;


GdkColor rgb_to_gdk(guint32 in)
{
	GdkColor out;
	out.red = ((in >> 16) & 255) << 8;
	out.green = ((in >> 8) & 255) << 8;
	out.blue = (in & 255) << 8;
	return out;
}	

GtkWidget* setup_scrollpane()
{
	// Gtk Adjustment params (all double): 
	//     Default bound, Lower bound, Upper bound, 
	//	   Step Increment, Page Increment, Page Size 
	GtkObject *x = gtk_adjustment_new(0.5, 0.5, 0.5, 1.0, 10.0, 100.0);
	GtkObject *y = gtk_adjustment_new(5000.0, 100.0, 1000.0, 1.0, 10.0, 100.0);
	GtkWidget *scrollpane = gtk_scrolled_window_new((GtkAdjustment*)x, (GtkAdjustment*)y);
	//gtk_window_set_resizable((GtkWindow*)scrollpane, FALSE); 
	return scrollpane;
}

void create_rows(GtkWidget *window, syntax **type)
{
	int i;
	GdkColor col;

	for(i=0; i<30; i++, (*type)++)
	{ 	
		(*type)->content = gtk_hbox_new(FALSE, 4);
		// Add the name label
		(*type)->name = gtk_label_new(SYNTAX_TYPES[i]);
		gtk_misc_set_alignment((GtkMisc*)(*type)->name, 0.0, 0.0);
		gtk_label_set_width_chars((GtkLabel*)(*type)->name, 16);   

		// Add foregroud and background colour 
		col = rgb_to_gdk(BASE_COL[i*2]);
		(*type)->fore = gtk_color_button_new_with_color(&col);
		col = rgb_to_gdk(BASE_COL[i*2+1]);
		(*type)->back = gtk_color_button_new_with_color(&col);

		// Add checkboxes
		(*type)->bold = gtk_check_button_new();
		(*type)->italic = gtk_check_button_new();
		(*type)->ulined = gtk_check_button_new();

		// Add components to the container
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->name);
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->fore);
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->back);
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->bold);
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->italic);
		gtk_container_add(GTK_CONTAINER((*type)->content), (*type)->ulined);
		gtk_widget_show((*type)->name);
		gtk_widget_show((*type)->fore);
		gtk_widget_show((*type)->back);
		gtk_widget_show((*type)->bold);
		gtk_widget_show((*type)->italic);
		gtk_widget_show((*type)->ulined);
		gtk_container_add(GTK_CONTAINER(window), (*type)->content);
		gtk_widget_show((*type)->content);
	}
}

static void destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

int main(int argc, char *argv[])
{
	gtk_init(&argc, &argv);

	// Create main window and apply some default setting
	GtkWindow *window = (GtkWindow*)gtk_window_new(GTK_WINDOW_TOPLEVEL);;
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(destroy), NULL);
	gtk_container_set_border_width(GTK_CONTAINER(window), 6);
	gtk_window_set_resizable(window, TRUE);     
	
	//Create a widget to hold window content	
	GtkWidget *main_panel = gtk_vbox_new(FALSE, 0);
	GtkWidget *scrollpane = setup_scrollpane(); 
	

	// Create widgets for each type of syntax highlighting
	syntax *type = malloc(sizeof(syntax)*30);
	create_rows(main_panel, &type);
	

	//gtk_container_add(GTK_CONTAINER(scrollpane), main_panel);	
	gtk_scrolled_window_add_with_viewport((GtkScrolledWindow*)scrollpane, main_panel);	
	gtk_container_add(GTK_CONTAINER(window), scrollpane);
	
	gtk_widget_show(scrollpane);
	gtk_widget_show(main_panel);
	gtk_widget_show((GtkWidget*)window);
	gtk_main();
	return 0;
}
``` 
If you want to test the program you will need to include a file with some constants declared in it:
```
const char *SYNTAX_TYPES[] = 
{
	"text", "selection", "cursor", "current-line", "line-numbers",
	"bracket-match", "bracket-mismatch", "right-margin", "search-match",
	"constant", "string", "special-char", "special-constant", "floating-point",
	"comment", "sheband", "doc-comment", 
	"identifier", "statement", "type", 
	"preprocessor", "error", "note", "underlined",
	"added-line", "removed-line", "changed-line",
	"diff-file", "location", "special-case"
};

const guint32 BASE_COL[] =
{
	0xFFFFFF,	0x000000,	// TEXT
	0xFF0000,	0x000000,	// SELECTION
	0x00FF00,	0x000000, 	// CURSOR
	0x0000FF,	0x000000, 	// CURRENT LINE
	0xFFFF00,	0x000000, 	// LINE-NUMBERS
	0x00FFFF,	0x000000,	// BRACKET MATCH 
	0xFF00FF,	0x000000,	// BRACKET MISMATCH
	0xFFFFFF,	0x000000,	// RIGHT MARGIN
	0xFFFFFF, 	0x000000, 	// SEARCH MATCH
	0xFFFFFF,	0x000000,	// CONSTANT
	0xFFFFFF, 	0x000000,	// STRING
	0xFFFFFF,	0x000000,	// SPECIAL CHAR
	0xFFFFFF, 	0x000000,	// SPECIAL CONSTANT
	0xFFFFFF, 	0x000000,	// FLOATING POINT
	0xFFFFFF, 	0x000000,	// COMMENT
	0xFFFFFF,	0x000000,	// SHEBAND
	0xFFFFFF,	0x000000,	// DOC COMMENT
	0xFFFFFF,	0x000000,	// IDENTIFIER
	0xFFFFFF,	0x000000,	// STATEMENT
	0xFFFFFF, 	0x000000,	// TYPE
	0xFFFFFF,	0x000000,	// PREPROCESSOR
	0xFFFFFF, 	0x000000,	// ERROR
	0xFFFFFF, 	0x000000, 	// NOTE
	0xFFFFFF,	0x000000,	// UNDERLINED
	0xFFFFFF, 	0x000000,	// ADDED LINE
	0xFFFFFF, 	0x000000, 	// REMOVED LINE
 	0xFFFFFF,	0x000000,	// CHANGED LINE
	0xFFFFFF,	0x000000,	// FILE
	0xFFFFFF,	0x000000,	// LOCATION
	0xFFFFFF, 	0x000000,	// SPECIAL CASE
};
```
Any suggestions on how I can fix this? 

I would like the defualt scrollpanel size to be something like 200*400 and only stretch vertically. Cheers.

---

### Post by mike_g on 2008-04-06
I found the answer to this, it seems you can set ay widgets size with:
```
gtk_widget_set_usize(widget, w, h);
```
Still dont know what the adjustments do even after reading through all the docs, lol. But it seems I can just pass in NULL and forget about it.

---

