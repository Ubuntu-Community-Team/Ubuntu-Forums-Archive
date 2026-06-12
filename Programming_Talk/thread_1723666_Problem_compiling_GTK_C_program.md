---
title: "Problem compiling GTK C program"
date: 2011-04-07
forum: Programming Talk
---

### Post by gauravbutola on 2011-04-07
I am learning programming I am familiar with C but don't have any knowledge of GTK so I am learning it from [developer.gnome.org]("http://developer.gnome.org/gnome-devel-demos/stable/image-viewer.c.html") This link [http://developer.gnome.org/gnome-devel-demos/stable/image-viewer.c.html](http://developer.gnome.org/gnome-devel-demos/stable/image-viewer.c.html)

I am using Anjuta as my IDE. I did totally fine until the **"Builiding the code for the first time" **
And then followed the instructions afterwards but when I finished writing the code in main.c , I was unable to Compile/Build it. 
I get the following error.
```
Building in directory: /home/gaurav/image-viewer/Debug/Debug/src
make image_viewer
CCLD   image_viewer
main.o: In function `create_window':
/home/gaurav/image-viewer/src/main.c:109: undefined reference to `gtk_box_new'
collect2: ld returned 1 exit status
make: *** [image_viewer] Error 1
Completed unsuccessfully
Total time taken: 0 secs
```

Here is how my main.c file looks like.

```
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <string.h>
#include <stdio.h>

#include <config.h>

#include <gtk/gtk.h>



/*
 * Standard gettext macros.
 */
#ifdef ENABLE_NLS
#  include <libintl.h>
#  undef _
#  define _(String) dgettext (PACKAGE, String)
#  ifdef gettext_noop
#    define N_(String) gettext_noop (String)
#  else
#    define N_(String) (String)
#  endif
#else
#  define textdomain(String) (String)
#  define gettext(String) (String)
#  define dgettext(Domain,Message) (Message)
#  define dcgettext(Domain,Message,Type) (Message)
#  define bindtextdomain(Domain,Directory) (Domain)
#  define _(String) (String)
#  define N_(String) (String)
#endif



#include "callbacks.h"

/* For testing propose use the local (not installed) ui file */
/* #define UI_FILE PACKAGE_DATA_DIR"/image_viewer/ui/image_viewer.ui" */
#define UI_FILE "src/image_viewer.ui"

#include <glib/gi18n.h>

	
static void
on_open_image (GtkButton* button, gpointer user_data)
{
	GtkWidget *image = GTK_WIDGET (user_data);
	GtkWidget *toplevel = gtk_widget_get_toplevel (image);
	GtkFileFilter *filter = gtk_file_filter_new ();
	GtkWidget *dialog = gtk_file_chooser_dialog_new (_("Open image"),
	                                                 GTK_WINDOW (toplevel),
	                                                 GTK_FILE_CHOOSER_ACTION_OPEN,
	                                                 GTK_STOCK_OK, GTK_RESPONSE_ACCEPT,
	                                                 GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
	                                                 NULL);

	gtk_file_filter_add_pixbuf_formats (filter);
	gtk_file_chooser_add_filter (GTK_FILE_CHOOSER (dialog),
	                             filter);
	
	switch (gtk_dialog_run (GTK_DIALOG (dialog)))
	{
		case GTK_RESPONSE_ACCEPT:
		{
			gchar *filename = 
				gtk_file_chooser_get_filename (GTK_FILE_CHOOSER (dialog));
			gtk_image_set_from_file (GTK_IMAGE (image), filename);
			break;
		}
		default:
			break;
	}
	gtk_widget_destroy (dialog);
}
	
static GtkWidget*
create_window (void)
{
	GtkWidget *window;
	GtkWidget *button;
	GtkWidget *image;
	GtkWidget *box;

	/* Set up the UI */
	window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title (GTK_WINDOW (window), "image-viewer-c");

	box = gtk_box_new (GTK_ORIENTATION_VERTICAL, 5);
	button = gtk_button_new_with_label (_("Open image"));
	image = gtk_image_new ();

	gtk_box_pack_start (GTK_BOX (box), image, TRUE, TRUE, 0);
	gtk_box_pack_start (GTK_BOX (box), button, FALSE, FALSE, 0);

	gtk_container_add (GTK_CONTAINER (window), box);

	/* Connect signals */

	/* Show open dialog when opening a file */
	g_signal_connect (button, "clicked", G_CALLBACK (on_open_image), image);
	
	/* Exit when the window is closed */
	g_signal_connect (window, "destroy", G_CALLBACK (gtk_main_quit), NULL);
	
	return window;
}


int
main (int argc, char *argv[])
{
 	GtkWidget *window;


#ifdef ENABLE_NLS
	bindtextdomain (GETTEXT_PACKAGE, PACKAGE_LOCALE_DIR);
	bind_textdomain_codeset (GETTEXT_PACKAGE, "UTF-8");
	textdomain (GETTEXT_PACKAGE);
#endif

	
	gtk_set_locale ();
	gtk_init (&argc, &argv);

	window = create_window ();
	gtk_widget_show (window);

	gtk_main ();
	return 0;
}

```


Help would be much appreciated.

Thanks 
Gaurav Butola

---

### Post by andrew1992 on 2011-04-07
GtkBox is not a gtk widget in itself...that's the problem. You have to specify horizontal or vertical, if you mean that kind of box.

---

### Post by SledgeHammer_999 on 2011-04-07
In the API docs there is no "gtk_box_new()" [link](http://developer.gnome.org/gtk/stable/GtkBox.html)

I think you meant gtk_vbox_new() [link](http://developer.gnome.org/gtk/stable/GtkVBox.html#gtk-vbox-new)

---

### Post by gauravbutola on 2011-04-08
> **SledgeHammer_999 said:**
> In the API docs there is no "gtk_box_new()" [link](http://developer.gnome.org/gtk/stable/GtkBox.html)

I think you meant gtk_vbox_new() [link](http://developer.gnome.org/gtk/stable/GtkVBox.html#gtk-vbox-new)

Thanks for the help, Now I am able to compile the project but when I run it, the output is not intended IIUC.

The output windows should be something like this which is able to open a picture [link]("http://developer.gnome.org/gnome-devel-demos/stable/media/image-viewer.png").
Whereas I am getting just a blank windows without any button (gtk_file_chooser) [http://i.imgur.com/6SRX4.png](http://i.imgur.com/6SRX4.png).
Can you help with that? I am very much new to this so I am kinda lost.

---

### Post by andrew1992 on 2011-04-08
It probably has something to do with your widgets not being contained in the window, or having their visibility property set to false, or something like that.  I've never written a gtk app purely in code, so I don't know a whole lot about how that works.  You should take a long, serious look at using Glade Interface Designer to layout your interface and set initial properties, because it will save yourself ALOT of code and debugging.

---

### Post by gauravbutola on 2011-04-08
> **andrew1992 said:**
> It probably has something to do with your widgets not being contained in the window, or having their visibility property set to false, or something like that.  I've never written a gtk app purely in code, so I don't know a whole lot about how that works.  You should take a long, serious look at using Glade Interface Designer to layout your interface and set initial properties, because it will save yourself ALOT of code and debugging.

Thanks for the suggestion Andrew, as I said I am new to GTK , so can you point me to some link where I can learn about Glad Interface Designer.

---

### Post by andrew1992 on 2011-04-08
Here is the link to the website: [http://glade.gnome.org/](http://glade.gnome.org/)
And an absolutely wonderful tutorial (covered in Python and C): [http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html)

---

### Post by SledgeHammer_999 on 2011-04-08
I didn't try this on your code. But put this line in create_window() just before returning:

```
gtk_widget_show_all(window);
```

This is necessary for the child widgets to be visible.

gtk_widget_show (window); -> it only 'shows' the window and not it's child widgets.

[gtk-widget-show-all()](http://developer.gnome.org/gtk/stable/GtkWidget.html#gtk-widget-show-all)
[gtk-widget-show()](http://developer.gnome.org/gtk/stable/GtkWidget.html#gtk-widget-show)

---

