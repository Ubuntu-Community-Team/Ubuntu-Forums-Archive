---
title: "need help with gtk programming"
date: 2010-10-12
forum: Programming Talk
---

### Post by c2tarun on 2010-10-12
hi friends
i am new to gtk programming.
as my college project, i have to create certain applications by gtk in gnome.
the problem is i have to create this application in hindi, can anyone please tell me how to show output in hindi or IISCI statndard.
+ i have to make certain changes in ubuntu. can anyone tell me from where i should start looking at the source of ubuntu.
thanx a lot

---

### Post by bouncingwilf on 2010-10-12
I'm not familiar with this subject but I believe the pango package is involved.

Bouncingwilf

---

### Post by worksofcraft on 2010-10-12
I found a "hello world" application that uses Gtk, but can't remember where I found it... anyway I used google translation service to get Hindi words for "Hello World!" and pasted those in to the source. You can simply copy the code and command to compile it into a program named a.out is on the first comment line.

If I find the source of the tutorial I'll come back and update meanwhile here it is:
[php]
// gcc -Wall -g hellohindi.c `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
#include <gtk/gtk.h>

/* This is a callback function. The data arguments are ignored
 * in this example. More on callbacks below. */
static void hello( GtkWidget *widget,
                   gpointer   data )
{
    g_print ("&#2344;&#2350;&#2360;&#2381;&#2340;&#2375; &#2357;&#2367;&#2358;&#2381;&#2357;!\n");
}

static gboolean delete_event( GtkWidget *widget,
                              GdkEvent  *event,
                              gpointer   data )
{
    /* If you return FALSE in the "delete-event" signal handler,
     * GTK will emit the "destroy" signal. Returning TRUE means
     * you don't want the window to be destroyed.
     * This is useful for popping up 'are you sure you want to quit?'
     * type dialogs. */

    g_print ("delete event occurred\n");

    /* Change TRUE to FALSE and the main window will be destroyed with
     * a "delete-event". */

    return FALSE;
}

/* Another callback */
static void destroy( GtkWidget *widget,
                     gpointer   data )
{
    gtk_main_quit ();
}

int main( int   argc,
          char *argv[] )
{
    /* GtkWidget is the storage type for widgets */
    GtkWidget *window;
    GtkWidget *button;
    
    /* This is called in all GTK applications. Arguments are parsed
     * from the command line and are returned to the application. */
    gtk_init (&argc, &argv);
    
    /* create a new window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    
    /* When the window is given the "delete-event" signal (this is given
     * by the window manager, usually by the "close" option, or on the
     * titlebar), we ask it to call the delete_event () function
     * as defined above. The data passed to the callback
     * function is NULL and is ignored in the callback function. */
    g_signal_connect (window, "delete-event",
		      G_CALLBACK (delete_event), NULL);
    
    /* Here we connect the "destroy" event to a signal handler.  
     * This event occurs when we call gtk_widget_destroy() on the window,
     * or if we return FALSE in the "delete-event" callback. */
    g_signal_connect (window, "destroy",
		      G_CALLBACK (destroy), NULL);
    
    /* Sets the border width of the window. */
    gtk_container_set_border_width (GTK_CONTAINER (window), 10);
    
    /* Creates a new button with the label "Hello World". */
    button = gtk_button_new_with_label ("&#2344;&#2350;&#2360;&#2381;&#2340;&#2375; &#2357;&#2367;&#2358;&#2381;&#2357;!");
    
    /* When the button receives the "clicked" signal, it will call the
     * function hello() passing it NULL as its argument.  The hello()
     * function is defined above. */
    g_signal_connect (button, "clicked",
		      G_CALLBACK (hello), NULL);
    
    /* This will cause the window to be destroyed by calling
     * gtk_widget_destroy(window) when "clicked".  Again, the destroy
     * signal could come from here, or the window manager. */
    g_signal_connect_swapped (button, "clicked",
			      G_CALLBACK (gtk_widget_destroy),
                              window);
    
    /* This packs the button into the window (a gtk container). */
    gtk_container_add (GTK_CONTAINER (window), button);
    
    /* The final step is to display this newly created widget. */
    gtk_widget_show (button);
    
    /* and the window */
    gtk_widget_show (window);
    
    /* All GTK applications must have a gtk_main(). Control ends here
     * and waits for an event to occur (like a key press or
     * mouse event). */
    gtk_main ();
    
    return 0;
}
[/php]

I hope that helps :)

---

