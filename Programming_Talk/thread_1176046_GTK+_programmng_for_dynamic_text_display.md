---
title: "GTK+ programmng for dynamic text display"
date: 2009-06-01
forum: Programming Talk
---

### Post by teohoeeng on 2009-06-01
**GTK+ programmng for dynamic text display** 
Hi, all.
I am very new to GTK+ 2.0. I just started to use it to build a very simple GUI for my robot under Ubuntu 7.10. I am trying to get the GTK+ to display my robot's sensors data at certain time intervals. Right now, I am using gtk_entry_get_text() and it can only displays once after the GUI is launched and the program waits at gtk_main().

I tried to create a timer handler to update the sensor data at 5Hz rate or even use another thread to do it, but the text won't change. It is always showing the very first text displayed when GUI is launched.

As I am very new to this GUI and do not wish to spend too much time in complicated GUI design as it is not my focus, is there a simple solution to dynamic numeric data display? 

Appreciate any help and advice. Thanks.

Regards
Ken

---

### Post by kknd on 2009-06-01
I don't know if I understood your problem, but only the main thread can manipulate the widgets.

So, if you have another thread and want to update the GUI, the simple way is to call g_iddle_add from the other thread, passing a callback that will be used to update the GUI. That callback will be called by GTK+ in the main thread, so it will (hopefully) work as expected.

---

### Post by teohoeeng on 2009-06-01
Thanks. To elaborate what I did unsuccessfully.
 
My timer handler is triggered every 0.2s and it wants update the numeric text (eg sensor data). The problem I realize is how can I use the gtk_g_connect() to connect this update mechanism to the callback function which will use gtk_set_text() to update the new text display. I tried to use any button I have to test out. It works, but I have to keep pressing the buttons to update the display. I want to make it automated at regular intervals based on my timer rate. 
 
How can I let the main thread for the GUI knows that I want to perform a callback at regular rate? I place the gtk_set_text() in the timer handler but it doesn't work. It seems to me that action has to be taken (ie mouse click or movement) before the GUI will update the display.

---

### Post by PmDematagoda on 2009-06-02
Could you try and post the code in question? It is quite difficult to figure out exactly what your problem is without it.

---

### Post by Linteg on 2009-06-02
I'm guessing that you want to have a label (or something similar) which is updated at a regular interval. If so, take a look at the following example:
[PHP]#include <glib.h>
#include <gtk/gtk.h>

#define FREQUENCY 5

static void     destroy (GtkWidget *widget, gpointer data);
static gboolean update_text (GtkWidget *label);

int
main (int argc, char **argv) 
{
	GtkWidget *window;
	GtkWidget *label;
	
	gtk_init (&argc, &argv);
	
	window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title (GTK_WINDOW(window), "Window");
	g_signal_connect (G_OBJECT(window), "destroy", G_CALLBACK(destroy), NULL);

	label = gtk_label_new ("Times updated: 0");
    gtk_container_add (GTK_CONTAINER (window), label);
	
	g_timeout_add (1000/FREQUENCY, (GSourceFunc)update_text, label);	
	gtk_widget_show_all (window);
	
	gtk_main ();
	
	return 0;
}

static gboolean
update_text (GtkWidget *label)
{
	gchar *text;
	static int i = 0;
	
	/* A prettier solution would proably be to remove the timeout when
	 * the window is closed */
	if (GTK_IS_LABEL(label))
	{
		text = g_strdup_printf ("Times updated: %i", ++i);
		gtk_label_set_text (GTK_LABEL(label), text);
		g_free (text);
		return TRUE;
	}
	/* Returning FALSE removes the timeout from the glib main loop */
	else
		return FALSE;
	
}

static void
destroy (GtkWidget *widget, gpointer data)
{
    gtk_main_quit ();
}[/PHP]

---

### Post by teohoeeng on 2009-06-02
Thanks. It works exactly what I need. g_timeout_add() is the missing key to my code. Now I can expand the code to make it update all those data I have on the GUI.  Thanks so much again!

---

