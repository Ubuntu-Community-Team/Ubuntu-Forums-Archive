---
title: "[SOLVED] GTK+:resize image when resizing window"
date: 2008-04-21
forum: Programming Talk
---

### Post by pacofvf on 2008-04-21
ok this is how i create my image, actually i don't know if there is a better way:
```

  GtkWidget *box,*label,*image,*button;
  GdkPixbuf *pixbuf;
  box=gtk_vbox_new (FALSE, 0);
  button=gtk_button_new();
  label=gtk_label_new("button 1");
  pixbuf=gdk_pixbuf_new_from_file("button1.jpg",NULL);
  pixbuf=gdk_pixbuf_scale_simple(pixbuf,50,50,GDK_INTERP_BILINEAR);
  image=gtk_image_new_from_pixbuf(pixbuf);
  gtk_button_set_image(GTK_BUTTON(button),image);
  gtk_box_pack_start (GTK_BOX (box), button, TRUE, TRUE, 0);
  gtk_box_pack_end (GTK_BOX (box), label, FALSE, TRUE, 0);

```
ok? i have my 50x50 image and i need to resize it if the window is resized. any idea? thanks.

---

### Post by sq377 on 2008-04-21
If you draw the widget on expose-events, it will be called every time they resize the window.  You can then grab the size of the widget and have it scale to that instead of 50,50.

---

### Post by pacofvf on 2008-04-23
> **sq377 said:**
> If you draw the widget on expose-events, it will be called every time they resize the window.  You can then grab the size of the widget and have it scale to that instead of 50,50.
this is what i have :
```

 #include <gtk/gtk.h>
#include <stdlib.h>
#include <stdio.h>
#include <glib.h>
#include <gdk-pixbuf/gdk-pixbuf.h>
#include <string.h>
int resized;
/* standard handlers */
gint delete_event(GtkWidget *widget, GdkEvent event, gpointer data)
{
   return FALSE;
}
void end_program(GtkWidget *widget, gpointer data)
{
   gtk_main_quit();
}
void render_image(GtkWidget *window, gpointer data)
{
  GtkImage *image;
  GtkButton *button;
  GdkPixbuf *orig_pixbuf, *new_pixbuf;
  gint orig_width, orig_height;
  gint new_width, new_height;
  gdouble zoom_value;
  if(resized!=0 && resized%2==0){
  image = (GtkImage *) data;
  /* get the original pixbuf dimensions */
  orig_pixbuf = (GdkPixbuf *)g_object_get_data(G_OBJECT(image), "orig&#8722;pixbuf");
  orig_width = gdk_pixbuf_get_width(orig_pixbuf);
  orig_height = gdk_pixbuf_get_height(orig_pixbuf);
  /* get adjuster&#8722;induced changes */
  zoom_value = 2;
  /* compute new size */
  new_width = (gint)(orig_width * zoom_value);
  new_height = (gint)(orig_height * zoom_value);
  /* prevent a height or width of 0 */
  new_width = MAX(1, new_width);
  new_height = MAX(1, new_height);
  /* scale the original pixbuf to the new dimensions
     (feel free to try other interpolation algorithms) */
  new_pixbuf = gdk_pixbuf_scale_simple(orig_pixbuf,
                                        new_width,
                                        new_height,
                                        GDK_INTERP_BILINEAR);
  /* display the new pixbuf in the image widget */
  g_object_set(image, "pixbuf", new_pixbuf, NULL);//->>>>segmentation fault
  /* reference to new_pixbuf is no longer necessary,
     the system may dispose of it when convenient */
  g_object_unref(new_pixbuf);
  }
  resized++;
}
int main(int argc, char **argv)
{
  GtkWindow *window;
  GtkHBox *hbox;
  GtkImage *image;
  GtkButton *button;
  GtkLabel *label;
  GdkPixbuf *orig_pixbuf;
  resized=0;
  /* initialize GTK+, create a window */
  gtk_init(&argc, &argv);
  window = g_object_new(GTK_TYPE_WINDOW,"title", "resize 2","default&#8722;width", 300,"default&#8722;height", 300,"border&#8722;width", 12,NULL);
  /* attach standard event handlers */
  g_signal_connect(window, "delete_event", G_CALLBACK(delete_event), NULL);
  g_signal_connect(window, "destroy", G_CALLBACK(end_program), NULL);
  /* create image widget and load a file */
  image = g_object_new(GTK_TYPE_IMAGE, "file", "sí.jpg", NULL);
  /* store the original pixbuf in the image widget data */
  g_object_get(image, "pixbuf", &orig_pixbuf, NULL);
  g_object_set_data(G_OBJECT(image), "orig&#8722;pixbuf", (gpointer)orig_pixbuf); 
  g_object_set(button, "image", image, NULL);
  /* install adjuster signal handlers */
  g_signal_connect(GTK_WIDGET(window), "size-request",
		   G_CALLBACK(render_image), (gpointer) image); 
  /* create a new HBox, pack the image and vboxes above */
  hbox = g_object_new(GTK_TYPE_HBOX, NULL);
  gtk_box_pack_start_defaults(GTK_BOX(hbox), GTK_WIDGET(image));
  /* pack everything into the window, show everything, start GTK+ main loop */
  gtk_container_add(GTK_CONTAINER(window), GTK_WIDGET(hbox));
  gtk_widget_show_all(GTK_WIDGET(window));
  gtk_main();
  return 0;
}

```
i have a segmentation fault in line 46:g_object_set(image, "pixbuf", new_pixbuf, NULL);

---

### Post by pacofvf on 2008-05-26
Well... i never found a real solution for this issue but something that always works is gtk_widget_destroy(button) and build it again.

---

### Post by sq377 on 2008-05-26
Here's how I would go about it.
Hope it helps.

```
#include <gtk/gtk.h>
#include <gdk-pixbuf/gdk-pixbuf.h>

gboolean resize_image(GtkWidget *widget, GdkEvent *event, GtkWidget *window)
{
	GdkPixbuf *pixbuf =	gtk_image_get_pixbuf(GTK_IMAGE(widget));
	if (pixbuf == NULL)
	{
		g_printerr("Failed to resize image\n");
		return 1;
	}
	
	printf("Width: %i\nHeight%i\n", widget->allocation.width, widget->allocation.height);
	
	pixbuf = gdk_pixbuf_scale_simple(pixbuf, widget->allocation.width, widget->allocation.height, GDK_INTERP_BILINEAR);
	
	gtk_image_set_from_pixbuf(GTK_IMAGE(widget), pixbuf);
	
	return FALSE;
}
int main(int argc, char **argv)
{
	GtkWidget *window = NULL;
	GtkWidget *image = NULL;

	if (argc < 2 || argc > 3)
	{
		g_printerr("Usage: %s <image>\n", argv[0]);
		return 1;
	}

	/* Initialize */
	gtk_init(&argc, &argv);
	
	/* Creat Widgets */
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	image = gtk_image_new_from_file(argv[1]);
	if (image == NULL)
	{
		g_printerr("Could not open \"%s\"\n", argv[1]);
		return 1;
	}
	
	/* attach standard event handlers */
	g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
	g_signal_connect(image, "expose-event", G_CALLBACK(resize_image), (gpointer)window);
	
	gtk_container_add(GTK_CONTAINER(window), image);
	gtk_widget_show_all(GTK_WIDGET(window));

	gtk_main();

	return 0;
}

```

---

### Post by pacofvf on 2008-05-28
thanks excellent, only one more question, This also may work if the widget that contains the image is a box right?

---

### Post by sq377 on 2008-05-28
As long as the box's packing options is set to expand, yes.

---

