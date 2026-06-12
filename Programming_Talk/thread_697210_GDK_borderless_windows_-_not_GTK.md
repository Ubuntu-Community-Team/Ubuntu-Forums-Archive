---
title: "GDK borderless windows - not GTK"
date: 2008-02-14
forum: Programming Talk
---

### Post by dosh on 2008-02-14
I have seen examples of Borderless windows using Xlib and using GTK. how would I go about it using GDK library? Any examples?:confused:

---

### Post by lnostdal on 2008-02-15
[http://library.gnome.org/devel/gtk/stable/GtkWindow.html#gtk-window-set-decorated](http://library.gnome.org/devel/gtk/stable/GtkWindow.html#gtk-window-set-decorated)

```

/*
  gcc -o gtk-helloworld -g -Wall `pkg-config --cflags --libs gtk+-2.0` gtk-helloworld.c
*/

#include <stdio.h>
#include <gtk/gtk.h>

void hello(GtkWidget* widget, gpointer data)
{
  printf("Hello World!\n");
}

int main(int argc, char* argv[])
{
  GtkWidget* window;
  GtkWidget* button;

  gtk_init(&argc, &argv);
  
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  button = gtk_button_new_with_label("Hello World");
  gtk_container_add(GTK_CONTAINER(window), button);
  gtk_window_set_decorated((GtkWindow*)window, 0);
  
  g_signal_connect(G_OBJECT(button), "clicked",
                   G_CALLBACK(hello), NULL);
  g_signal_connect(G_OBJECT(window), "delete-event",
                   G_CALLBACK(gtk_main_quit), NULL);

  gtk_widget_show_all(window);
  gtk_main();
  return(0);
}

```

edit: you can still move stuff around my holding *alt* in while cliking left mouse button and dragging ... =)

---

### Post by lnostdal on 2008-02-15
ow, gdk only? .. then [http://library.gnome.org/devel/gdk/2.8/gdk-Windows.html#gdk-window-set-decorations](http://library.gnome.org/devel/gdk/2.8/gdk-Windows.html#gdk-window-set-decorations)

---

### Post by dosh on 2008-02-15
Thanks Inostdal
however that is using GTK I'm trying to use just the GDK library.
I've tried converting them but things like the Gtk-container is one thing not directly in the GDK library

---

### Post by lnostdal on 2008-02-15
what do you mean by "converting them"? .. did you see my previous reply btw.?

---

### Post by dosh on 2008-02-16
Sorry I missed that posting. What I meant by converting was using the equivalent GDK code, though sometimes I haven't been able to find some equivalent GDK code. Thanks for the decorations reference I was able to get a window with no Titlebar and no Borders. Now I should be able to use a gdk_window_shape_combine_mask to get a shaped window. Would this be right?

---

### Post by thenasko on 2008-08-21
Were you able to accomplish the task by GDK alone. I am looking for something similar currently and would appreciate it if you post code.

Thanks in advance.

---

