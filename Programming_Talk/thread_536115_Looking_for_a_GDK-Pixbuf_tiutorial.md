---
title: "Looking for a GDK-Pixbuf tiutorial"
date: 2007-08-27
forum: Programming Talk
---

### Post by cybrid on 2007-08-27
Just that. I've been searching through google and the forums and haven't been able to find a nice tutorial. I want to use images in gtk apps and after going through part of the gtk2.0 tutorial I think that's the way to go. If someone could point me to a good tutorial, please .

Thanks in advance.

---

### Post by AlexThomson_NZ on 2007-08-27
If you seach for gtk tutorial, you should be able to find the official tutorial (sorry, don't have the link here).  It's reposted everywhere, and at the end is a simple paint program that uses this.

I'll post back when I get to work, and give you some of my own sample code if you like.

---

### Post by cybrid on 2007-08-27
Hey, thanks for the help. Currently I'm following the "official" gtk2.0 tutorial. And I just wanted to insert an image in a window. Maybe creating a hbox and packing the image in it?. like any other widget?.

---

### Post by AlexThomson_NZ on 2007-08-27
Yep that's the one ([http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)) I alluded to.

Here's a code except from a program I have done:
```

// TODO: Calculate & save normals
// TODO: Save .OBJ files properly
// TODO: Give a default to the Save As screen

#include "global.h"
#include "preferences.h"
#include "save.h"
#include "generate.h"

int main(int argc, char **argv) 
{
	
	GtkWidget *window1;
	gtk_init(&argc, &argv);
	
	size_grid = 256;
	pm_image = NULL;
	pm_parent = NULL;
    
	glade_init();
	
    
	xml_main = glade_xml_new(FILENAME, ROOTNODE, NULL);
	glade_xml_signal_autoconnect (xml_main);
	xml_prefs = glade_xml_new(FILENAME, PREFNODE, NULL);
	glade_xml_signal_autoconnect (xml_prefs);
	xml_about = glade_xml_new(FILENAME, ABOUTNODE, NULL);
	glade_xml_signal_autoconnect (xml_about);
	xml_save = glade_xml_new(FILENAME, SAVENODE, NULL);
	glade_xml_signal_autoconnect (xml_save);
	xml_fc = glade_xml_new(FILENAME, FCNODE, NULL);
	glade_xml_signal_autoconnect (xml_fc);

	GtkWidget *cb;
	cb = glade_xml_get_widget (xml_save, "cb_filetype");
	gtk_combo_box_set_active(GTK_COMBO_BOX(cb), 0);
	cb = glade_xml_get_widget (xml_save, "cb_gfxformat");
	gtk_combo_box_set_active(GTK_COMBO_BOX(cb), 0);
	   
	window1 = glade_xml_get_widget (xml_main, "window_main");
	gtk_widget_show (window1);

    if (!xml_main) {
        g_warning("something bad happened while creating the interface");
        return 1;
    }
	
	
	set_statusbar("Select 'Generate' to create a height-map");
	
	gtk_main();

    return 0;

}
// ********************************************************************
// Clear any existing drawables and update
// ********************************************************************
void new_image(gboolean clear_image)
{
	GtkWidget *drw;
	drw = glade_xml_get_widget (xml_main, "drawingarea1");
	
	GdkRectangle *area = malloc(sizeof(GdkRectangle));
	area->height = drw->allocation.height;
	area->width = drw->allocation.width;
	area->x = 0;
	area->y = 0;
	
	int width = drw->allocation.width;
	int height = drw->allocation.height;
	int start_x = (width/2)-(size_grid/2);
	int start_y = (height/2)-(size_grid/2);
	
	if (pm_parent)
		g_object_unref (pm_parent);
		
	if (pm_image && clear_image == TRUE)
		g_object_unref (pm_image);

	// Clear the whole drawing area and box the outline black box
	pm_parent = gdk_pixmap_new (drw->window, width, height,-1);
	gdk_draw_rectangle (pm_parent, drw->style->white_gc, TRUE, 0, 0, width, height);
	gdk_draw_rectangle (pm_parent, drw->style->black_gc, FALSE, start_x-1, start_y-1, size_grid+1, size_grid+1);
	
	// Clear the inner part
	if (clear_image == TRUE)
	{
		pm_image = gdk_pixmap_new  (drw->window, size_grid, size_grid,-1);
		gdk_draw_rectangle (pm_image, drw->style->white_gc, TRUE, 0, 0, size_grid, size_grid);
	}
   	
	if (pm_image != NULL)
		gdk_draw_drawable (pm_parent, drw->style->fg_gc[GTK_WIDGET_STATE (drw)], pm_image, 0, 0, start_x, start_y, size_grid, size_grid);
	
	gtk_widget_draw(drw, area);
	
	free(area);
}

// ********************************************************************
// Show the about box
// ********************************************************************
void activate_about()
{
	GtkWidget *dialog1;
	dialog1 = glade_xml_get_widget (xml_about, "dialog_about");
	gtk_about_dialog_set_name(GTK_ABOUT_DIALOG(dialog1), PROGRAM_NAME);
	gtk_about_dialog_set_version(GTK_ABOUT_DIALOG(dialog1), PROGRAM_VERSION);
	gtk_widget_show (dialog1);
}

// ********************************************************************
// Close the about box
// ********************************************************************
void close_about()
{
	GtkWidget *dialog1;
	dialog1 = glade_xml_get_widget (xml_about, "dialog_about");
	gtk_widget_hide (dialog1);
}

// ********************************************************************
// Called when application starts up - use it to create a (blank) image
// ********************************************************************
void configure_drawing_area ( GtkWidget *widget, GdkEventConfigure *event)
{
	new_image(FALSE);
    return;
}

// ********************************************************************
// Called when redrawing the drawing area (ie. windows moves over it, etc.)
// ********************************************************************
void expose_drawing_area ( GtkWidget *widget, GdkEventExpose *event )
{
   	if (pm_parent) {
	    gdk_draw_drawable (widget->window, widget->style->fg_gc[GTK_WIDGET_STATE (widget)], pm_parent, event->area.x, event->area.y, event->area.x, event->area.y, event->area.width, event->area.height);
	}
	if (pm_image) {
		draw_pic(widget);
	}
    return;
}

// ********************************************************************
// Draw the generated image
// ********************************************************************
void draw_pic ( GtkWidget *widget )
{
	int width = widget->allocation.width;
	int height = widget->allocation.height;
	int start_x = (width/2)-(size_grid/2);
	int start_y = (height/2)-(size_grid/2);

    gdk_draw_drawable (widget->window, widget->style->fg_gc[GTK_WIDGET_STATE (widget)], pm_image, 0, 0, start_x, start_y, size_grid, size_grid);
}

// ********************************************************************
// Quit the application
// ********************************************************************
void activate_quit()
{
	if (pm_parent)
		g_object_unref (pm_parent);
		
	if (pm_image)
		g_object_unref (pm_image);
		
	if (map_data)
		free(map_data);
		
	gtk_exit(0);
}

void set_statusbar(gchar *text)
{
	GtkWidget *sb;
	sb = glade_xml_get_widget (xml_main, "statusbar1");
	guint sb_context = gtk_statusbar_get_context_id (GTK_STATUSBAR (sb), "???");
	gtk_statusbar_push (GTK_STATUSBAR (sb), sb_context, text);
}

```

It's quite complicatd though, even to do simple things, as you have to handle what happens when it gets obscured, etc.

---

### Post by duff on 2007-08-27
> **cybrid said:**
> Hey, thanks for the help. Currently I'm following the "official" gtk2.0 tutorial. And I just wanted to insert an image in a window. Maybe creating a hbox and packing the image in it?. like any other widget?.

Here's the PyGTK way.  Should be simple enough to convert to any other language you plan to use.

```
import gtk
import gtk.gdk

w = gtk.Window ()
pixbuf = gtk.gdk.pixbuf_new_from_file ('/usr/share/pixmaps/gnome-computer.png')
i = gtk.Image ()
i.set_from_pixbuf (pixbuf)
w.add (i)
w.show_all ()
gtk.main ()
```

If you're using C, there's any even easier way by using [gtk_image_new_from_file ()]("http://library.gnome.org/devel/gtk/unstable/GtkImage.html#gtk-image-new-from-file")

---

### Post by cybrid on 2007-08-29
Thank you both.  The code samples have been really helpful. But changing of theme; it could be just me, but there seems to be a lack of gtk learning related material. I know the gtk 2.0 tutorial is great but, I've found a very small amount of additional resources besides the mentioned tutorial; do you agree?.

---

### Post by loell on 2007-08-29
are you learning pygtk or c/gtk?

---

### Post by Thyme on 2007-08-29
I'm also following that tutorials and came across this somewhere in there:

GtkWidget *image;
GdkPixbuf *pixbuf;
GError *error = NULL;

pixbuf = gdk_pixbuf_new_from_file("/home/thyme/icons/test.png", &error);
image = gtk_image_new_from_pixbuf(pixbuf);

Hope this helps :)

---

### Post by cybrid on 2007-08-29
> **loell said:**
> are you learning pygtk or c/gtk?

C / GTK. 

Oh and thank you for the code Thyme :D .

---

### Post by Thyme on 2007-08-29
No problem :)

---

### Post by cybrid on 2007-08-29
Hmmm, does pixbuf support GIF images?.

---

### Post by duff on 2007-08-29
Run
```
# python -c 'import gtk.gdk; print gtk.gdk.pixbuf_get_formats()'
```

from the command line to set which formats your setup supports.

---

### Post by leibowitz on 2007-08-29
I agree, lack of GTK learning material.


I'm trying to produce a new tutorial, but, it takes time.. and I'm not an english native, so I will probably need someone to re-rewrite part of it.

If anyone is interested...

---

### Post by cybrid on 2007-08-29
> **duff said:**
> Run
```
# python -c 'import gtk.gdk; print gtk.gdk.pixbuf_get_formats()'
```

from the command line to set which formats your setup supports.

Thanks :D 

And leibowitz, at least there is someone doing something about it. I know a lot of people has gone the glade way but I don't find direct GTK that difficult and the speed gain is significant.

---

