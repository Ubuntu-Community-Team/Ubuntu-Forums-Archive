---
title: "[SOLVED] Gtk beginner - open another window?"
date: 2008-05-25
forum: Programming Talk
---

### Post by anewguy on 2008-05-25
I have an application I have been working on (BTW - thanks to everyone here who replied to my previous cries for help!!) that uses Gtk, and this is my first Gtk project.

I have the main window with buttons that perform various functions.  I also would like to be able to press a button and have another new window appear with it's own set of buttons.  I've tried to do some research, and I'm thinking I have to declare a window with Gtk window popup, but not positive.  I'm also wondering about the actual processing of this window - I assume I would need to hide the main window then show it again upon exit or destroy.  Do I need to do anything different besides just letting the original gtk main run (i.e., do I need another "process me" loop like gtk main except for the popup window?

I know that once I get 1 figured out then doing cascading windows will be an easy step from there.  Just need some advice on this first attempt.

Thanks in advance!!  :):)

---

### Post by mike_g on 2008-05-25
I used gtk_dialog_new_with_buttons in the past to create a popup window. Then you just set the g_signal_connect on the button to run the function that creates the child window.

---

### Post by anewguy on 2008-05-25
I've used the message dialog to do popups for things like yes/no, continue/cancel, etc..  In this case, I want an entirely different window, with many buttons on that window.  I've gotten as far as hiding the main window and showing the new window, however I don't see any of the widgets on the new window.   Maybe I actually need to create it as another main window not as a popup.

---

### Post by MicahCarrick on 2008-05-25
If you're saying that your application can have multiple windows (all the same) then what we often do is we have a list of windows associated with out application. You can have a GList containing GtkWindows in a struct that you pass around as your application's data.

Here's an example. Each window has a button on it. If you press that button, another window that looks the same is opened. The application quits when ALL of the windows are closed.

```
#include <gtk/gtk.h>

typedef struct
{
        GSList *windows;
        
        /* etc... whatever application vars you need */
} MyApp;


void 
on_window_destroy (GtkWidget *widget, MyApp *app)
{
        app->windows = g_slist_remove (app->windows, widget);
        
        if (g_slist_length (app->windows) == 0)
        {
                /* last window was closed... exit */
                
                g_debug ("Exiting...");
                g_slist_free (app->windows);
                gtk_main_quit ();
        }
}

void
on_add_button_clicked (GtkWidget *widget, MyApp *app)
{
        GtkWidget *window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
        GtkWidget *button = gtk_button_new_from_stock (GTK_STOCK_ADD);
        gchar *title;
        
        /* add window to list */
        
        app->windows = g_slist_prepend (app->windows, window);
        
        /* setup window and pack a button into it */
        
        gtk_container_set_border_width (GTK_CONTAINER (window), 25);
        gtk_container_add (GTK_CONTAINER (window), button);
        title = g_strdup_printf ("Window %d", g_slist_length (app->windows));
        gtk_window_set_title (GTK_WINDOW (window), title);
        g_free (title);
        
        /* connect callbacks to signals */
        
        g_signal_connect (G_OBJECT (window), "destroy", 
                          G_CALLBACK (on_window_destroy), app);
        
        g_signal_connect (G_OBJECT (button), "clicked", 
                          G_CALLBACK (on_add_button_clicked), app);
                                       
        
        gtk_widget_show_all (window);     
}

int
main (int argc, char *argv[])
{
        MyApp *app;
        
        gtk_init (&argc, &argv);
        app = g_slice_new (MyApp);
        app->windows = NULL;
        
        /* create first window */
        on_add_button_clicked (NULL, app);
        
        gtk_main ();
        g_slice_free (MyApp, app);
        
        return 0;               
}

```

---

### Post by anewguy on 2008-05-25
Thanks, Micah.  For now, my C "skills" haven't recovered enough from 12+ years of no use to follow your example - you did great, I'm just ignorant for now.

However, I did figure out how to do what I wanted.  I changed my second window to TOPLEVEL instead of popup, then just defined, packed and show'd everything except the window in main.c.  In the callout function, it just hides the main window and show_all of the second window.  The callout for cancelling the second window then just hides itself and shows the main window.  It seems to do what I want, just maybe not quite as good of code as it should be.

Thanks again!!  :)
Dave

---

