---
title: "Using GTK+ under Windows, need help"
date: 2006-03-24
forum: Programming Talk
---

### Post by tomcio on 2006-03-24
Hi there!

I'm going to make port of my program for Windows. I tried to use DevC++ and GTK+ port from [http://gladewin32.sourceforge.net/](http://gladewin32.sourceforge.net/). i have even compiled and run a few small programs under Windows, but I have problems with using GTK+ and GThread, because it doesb't work for me :( 
Simple mulyi threadd applications for console works great, but I'm not able to run multi thread GTK+ program, this is code of my application:
[SIZE="1"][INDENT]
#include <stdlib.h>
#include <gtk/gtk.h>


void create_window (void)

{
  GtkWidget *dialog = NULL;

  dialog = gtk_dialog_new ();
  gtk_widget_show (dialog);
}

int main (int argc, char *argv[])

{
  GtkWidget *window;

  g_thread_init (NULL);

  gdk_threads_init ();
  gdk_threads_enter ();

  gtk_init (&argc, &argv);
  g_thread_create (create_window, NULL, FALSE, NULL);

  gtk_main ();
  gdk_threads_leave ();

  return 0;
}[/INDENT][/SIZE]

like I said GThread works in console applications. 
Can someone try to compile this code? I'm new in programming for windows, for now I had only write programs for Linux.

Maybe I have wrong flags?
Later I post messages, whiich this programs sends to console.
I tested in on GTK+ 2.6.14, 2.6.10-RC1 and older 2.4.x from [http://gladewin32.sourceforge.net/](http://gladewin32.sourceforge.net/)

---

