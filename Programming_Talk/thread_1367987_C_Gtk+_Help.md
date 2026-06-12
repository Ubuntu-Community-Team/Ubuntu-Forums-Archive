---
title: "C Gtk+ Help"
date: 2009-12-30
forum: Programming Talk
---

### Post by nathan726 on 2009-12-30
I've been trying to create a very basic animation - the user should click inside the window and it will then turn green... then after a second it should turn back to the original color (but it doesn't).

Either gtk_widget_queue_draw() isn't doing it's job or I am doing something wrong here...

```
/* compiles with: gcc -o filename $(pkg-config --cflags --libs gtk+-2.0 ) filename.c */
#include <gtk/gtk.h>
#include <pthread.h>

float bar_r = 0.1, bar_g = 0.1, bar_b = 0.3, bar_a = 0.1;
int running = 1;

GtkWidget *window;
GtkWidget *d_area;

static gboolean on_expose_event(GtkWidget *widget, GdkEventExpose *event, gpointer data)
{
  cairo_t *cr;
  cr = gdk_cairo_create (widget->window);

  cairo_set_source_rgba(cr, bar_r, bar_g, bar_b, bar_a);
  cairo_set_line_width (cr, 40.0);
  cairo_move_to(cr, 20, 0);
  cairo_line_to(cr, 20, 500);
  cairo_move_to(cr, 220, 0);
  cairo_line_to(cr, 220, 500);
  cairo_stroke(cr);

  cairo_destroy(cr);

  return FALSE;
}

void *reset_colors()
{
  g_usleep(1000000);

  bar_r = 0.1;
  bar_g = 0.1;
  bar_b = 0.3;
  bar_a = 0.1;

  gtk_widget_queue_draw(d_area);
}

gboolean clicked(GtkWidget *widget, GdkEventButton *event, gpointer user_data)
{
  if (event->button == 1)
  {
    bar_r = 0.1;
    bar_g = 1;
    bar_b = 0.1;
    bar_a = 1;
    gtk_widget_queue_draw(d_area);

    pthread_t thread1;
    pthread_create(&thread1,NULL,reset_colors,NULL);
  }
  return TRUE;
}

int main (int argc, char *argv[])
{
  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_add_events (window, GDK_BUTTON_PRESS_MASK);

  d_area = gtk_drawing_area_new();
  gtk_widget_set_size_request (d_area, 240, 500);
  gtk_container_add(GTK_CONTAINER(window), d_area);

  g_signal_connect(d_area, "expose-event", G_CALLBACK (on_expose_event), NULL);
  g_signal_connect(window, "destroy", G_CALLBACK (gtk_main_quit), NULL);
  g_signal_connect(window, "button-press-event", G_CALLBACK(clicked), NULL);

  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);

  gtk_widget_show_all(window);
  gtk_main();

  running = 0;
  return 0;
}
```

---

### Post by nathan726 on 2009-12-30
GTK+ is "thread aware" but not thread safe.

This page should help anyone else who has the same problem:
[http://www.gnu.org/software/guile-gnome/docs/gdk/html/Threads.html](http://www.gnu.org/software/guile-gnome/docs/gdk/html/Threads.html)

---

