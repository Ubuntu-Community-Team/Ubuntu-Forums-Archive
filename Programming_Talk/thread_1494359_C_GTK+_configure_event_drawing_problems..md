---
title: "C GTK+ configure_event drawing problems."
date: 2010-05-26
forum: Programming Talk
---

### Post by superrikku on 2010-05-26
I am having some trouble writing a basic image viewing program. I stripped down what I have to this bit of problematic code:
[PHP]
#include <gtk/gtk.h>
#include <gdk-pixbuf/gdk-pixbuf.h>

static GdkPixbuf *image = NULL;
static guint width = 0;
static guint height = 0;
static gboolean loaded = FALSE;
static gchar *filename = NULL;

static gboolean reload_image(GtkWidget *widget) {
    if (!loaded) {
        image = gdk_pixbuf_new_from_file(filename, NULL);
        if (GDK_IS_PIXBUF(image)) {
            loaded = TRUE;
        } else {
            loaded = FALSE;
            return FALSE;
            /* faaaaailure */
        }
    }
    gdk_draw_pixbuf(widget->window, NULL, image, 0, 0, 0, 0, width, height, GDK_RGB_DITHER_NORMAL, 0, 0);
    return TRUE;
    /* success! */
}

static gboolean configure_event_cb(GtkWidget *widget, GdkEventConfigure *event) {
    gtk_window_get_size(GTK_WINDOW(widget), &width, &height);
    reload_image(widget);
    /* let handling continue */
    return FALSE;
}

int main(int argc, char **argv) {
    gtk_init(&argc, &argv);
    if (argc != 2) return 1;
    filename = argv[1];
    GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_widget_add_events(window, GDK_CONFIGURE);
    g_signal_connect(G_OBJECT(window), "delete_event", G_CALLBACK(gtk_main_quit), NULL);
    g_signal_connect(G_OBJECT(window), "configure_event", G_CALLBACK(configure_event_cb), NULL);
    gtk_widget_show(window);
    gtk_main();
    return 0;
}
[/PHP]

The problem is that when the program is first run (./iv image.jpg), the image is not displayed. Once another configure_event is triggered by moving the window or resizing it, the image or part of the image will load. If the window is resized, then the image will only load to the previous size of the window. If I run the program, it loads with a size of 200x200, blank. When it is resized, lets say to 300x300, the partial image appears, occupying the top-left 200x200 space. I have used gdb to check the values of the width and height variables, and during the configure event for such a resize, the variables are immediately set to 300 and 300, yet the image is drawn to the 200x200 block. Only after the next configure event is the pixbuf drawn properly, filling the 300x300 space. This is even more problematic, as it will still draw in 300x300 if the configure event is triggered by a resize to an even larger size. Compiling and running the program should immediately show what is happening.

Thanks ahead of time for any help =)

---

### Post by superrikku on 2010-05-30
Bump. I really need help with this, cause it doesn't make any sense =(

---

### Post by mali2297 on 2010-05-30
You need to write a callback to an "expose" event as well. You can then force the widget to redraw itself by calling [gtk-widget-queue-draw]("http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-queue-draw") or something equivalent.

---

### Post by superrikku on 2010-05-31
That definitely sounds like it will do the trick! I'll give it a shot. Thanks so much!

---

