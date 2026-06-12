---
title: "Drawing SVG with Cairo"
date: 2012-09-11
forum: Programming Talk
---

### Post by red_hax0r on 2012-09-11
I can't figure out how to draw an SVG file with Cairo in C.  Maybe I'm not linking with the right libraries.  Right now I'm using pkg-config with gtk+-2.0 and librsvg-2.0.  

Here's my code that I'm working with:

```

#include <gtk/gtk.h>
#include <librsvg/rsvg.h>
#include <librsvg/rsvg-cairo.h>

RsvgHandle* handle;

static gboolean
on_expose_event(GtkWidget *widget,
    GdkEventExpose *event,
    gpointer data)
{
  cairo_t *cr;

  cr = gdk_cairo_create (widget->window);

  rsvg_handle_render_cairo(handle, cr);
  cairo_paint(cr);

  cairo_destroy(cr);

  return FALSE;
}


int main(int argc, char *argv[])
{
  GtkWidget *window;
  GtkWidget *statusbar;
  GtkWidget *vbox;
  GtkWidget *fixed;

  //image = cairo_image_surface_create_from_png("plaveckycastle.png");
  g_type_init();

  GError* e = NULL;
  handle = rsvg_handle_new_from_file("dondorf.svg", &e);
  if(e != NULL)
    return 1;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  statusbar = gtk_statusbar_new();

  vbox = gtk_vbox_new(FALSE, 2);

  fixed = gtk_fixed_new();

  gtk_container_add(GTK_CONTAINER(window), vbox);

  gtk_box_pack_start(GTK_BOX(vbox), fixed, TRUE, TRUE, 1);
  gtk_box_pack_start(GTK_BOX(vbox), statusbar, FALSE, TRUE, 1);

  gchar *str;
  str = g_strdup("Status");


  gtk_statusbar_push(GTK_STATUSBAR(statusbar),
          gtk_statusbar_get_context_id(GTK_STATUSBAR(statusbar), str), str);
  g_free(str);

  g_signal_connect(fixed, "expose-event",
      G_CALLBACK (on_expose_event), NULL);
  g_signal_connect(window, "destroy",
      G_CALLBACK (gtk_main_quit), NULL);

  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  //gtk_window_set_resizable(GTK_WINDOW(window), FALSE);

  gtk_widget_set_size_request(window, 300, 245);
  gtk_widget_set_app_paintable(fixed, TRUE);

  gtk_widget_show_all(window);

  gtk_main();

  return 0;
}

```

The errors (link errors):
> 
In function `on_expose_event':
undefined reference to `rsvg_handle_render_cairo'
In function `main':
undefined reference to `rsvg_handle_new_from_file'


---

### Post by red_hax0r on 2012-09-11
Okay, I got it to work.  Apparently in Code::Blocks you have to specify --libs in the linker options and --cflags in the compiler options.  

After I got it compiled, it started showing only black in the window.  So I removed the 'cairo_paint(cr);' line and it worked.  Apparently it paints directly to the window in one shot with the rsvg_handle_render_cairo() function.

---

