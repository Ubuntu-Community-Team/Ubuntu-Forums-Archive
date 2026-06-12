---
title: "Mking a mess with GTK"
date: 2008-04-05
forum: Programming Talk
---

### Post by mike_g on 2008-04-05
I'm playing around with GTK for the first time. I dont really know what I'm doing here o_0. Heres my code:
```
#include <gtk/gtk.h>

static void destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

void popup(gchar *message, GtkWidget *parent) 
{
   GtkWidget *dialog, *label;
   /* Create the widgets */
  [COLOR="Red"] dialog = gtk_dialog_new_with_buttons("Message", parent, GTK_DIALOG_DESTROY_WITH_PARENT, 
										GTK_STOCK_OK, GTK_RESPONSE_NONE, NULL);[/COLOR]
   label = gtk_label_new (message);   
   /* Ensure that the dialog box is destroyed when the user responds. */
   g_signal_connect_swapped(dialog, "response", G_CALLBACK(gtk_widget_destroy), dialog);
   /* Add the label, and show everything we've added to the dialog. */
   gtk_container_add (GTK_CONTAINER (GTK_DIALOG(dialog)->vbox), label);
   gtk_widget_show_all(dialog);
}

int main(int argc, char *argv[])
{
	GtkWidget *window, *button;

	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

	g_signal_connect(G_OBJECT(window), "delete_event", G_CALLBACK(destroy), NULL);
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(destroy), NULL);
	gtk_container_set_border_width(GTK_CONTAINER(window), 10);

	button = gtk_button_new_with_label("Hello World");
	g_signal_connect(G_OBJECT(button), "clicked", [COLOR="Red"]G_CALLBACK(popup("Boo!", window)[/COLOR]), NULL);

	gtk_container_add(GTK_CONTAINER(window), button);
	gtk_widget_show(button);
	gtk_widget_show(window);
	gtk_main();
	return 0;
}
``` 
Basicaly i'm trying to make it so that when you click a button a popup appears. Gcc gives me the following output when I compile:
```
main.c: In function &#8216;popup&#8217;:
main.c:21: warning: passing argument 2 of &#8216;gtk_dialog_new_with_buttons&#8217; from incompatible pointer type
main.c: In function &#8216;main&#8217;:
main.c:43: error: void value not ignored as it ought to be
```
I think the problem is that I'm using G_CALLBACK wrong, tbh I dont even know what it does but it seems as if you cant put a function with arguments in it. Anyway I highlighted the bad bits red. Can someone tell me whats going on here? Cheers.

---

### Post by lnostdal on 2008-04-05
[http://developer.gimp.org/api/2.0/gtk/GtkDialog.html#gtk-dialog-new-with-buttons](http://developer.gimp.org/api/2.0/gtk/GtkDialog.html#gtk-dialog-new-with-buttons)

```

GtkWidget*          gtk_dialog_new_with_buttons         (const gchar *title,
                                                         GtkWindow *parent,
                                                         GtkDialogFlags flags,
                                                         const gchar *first_button_text,
                                                         ...);

```

notice the type of the parent parameter .. and compare with the type you use

---

### Post by lnostdal on 2008-04-05
hm .. i think G_CALLBACK only accept 1 argument .. but its a (C) macro, so who knows (i'm too lazy to check/confirm atm.)

---

### Post by mike_g on 2008-04-05
Yeah from what I can tell G_CALLBACK takes a function pointer. I also found that its possible to use GTK_WINDOW_TOPLEVEL in place of the pointer, which solved my problem, but I'll remember that its a window, not widget it takes. Cheers.

So far I have a version that compiles without warnings or segfaulting, my only problem i that I dont know how to send my message into the popup function:
```
#include <gtk/gtk.h>

static void destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

static gboolean popup(GtkWidget *widget, gpointer data) 
{
   GtkWidget *dialog, *label;
   /* Create the widgets */
   dialog = gtk_dialog_new_with_buttons("Message", GTK_WINDOW_TOPLEVEL, 	 
 									  GTK_DIALOG_DESTROY_WITH_PARENT, 
									  GTK_STOCK_OK, GTK_RESPONSE_NONE, NULL);
   label = gtk_label_new (data);   
   /* Ensure that the dialog box is destroyed when the user responds. */
   g_signal_connect_swapped(dialog, "response", G_CALLBACK(gtk_widget_destroy), dialog);
   /* Add the label, and show everything we've added to the dialog. */
   gtk_container_add (GTK_CONTAINER (GTK_DIALOG(dialog)->vbox), label);
   gtk_widget_show_all(dialog);
}

int main(int argc, char *argv[])
{
	GtkWidget *window, *button;

	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

	g_signal_connect(G_OBJECT(window), "delete_event", G_CALLBACK(destroy), NULL);
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(destroy), NULL);
	gtk_container_set_border_width(GTK_CONTAINER(window), 10);

	button = gtk_button_new_with_label("Hello World");
	g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(popup), NULL);

	gtk_container_add(GTK_CONTAINER(window), button);
	gtk_widget_show(button);
	gtk_widget_show(window);
	gtk_main();
	return 0;
}
```
AFAIK I never had to deal with function pointers before. How would I set the text for the gpointer (basically a void pointer) that passes data into the popup function?

---

### Post by lnostdal on 2008-04-05
see the API docs for g_signal_connect .. you can pass data to the handlers (you are currently supplying it with NULL)

---

### Post by mike_g on 2008-04-05
Lol, that was pretty obvios actully. Although I would say that now I know ;) Thanks.

---

