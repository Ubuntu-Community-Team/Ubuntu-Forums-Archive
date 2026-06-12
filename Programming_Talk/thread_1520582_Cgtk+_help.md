---
title: "C/gtk+ help"
date: 2010-06-29
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-06-29
I'm finally starting into gtk+ programming! I am trying to make a simple program to do stuff like ping and traceroute, then display the output as a "gtk_message_dialog" or something else if you have any ideas. the problem is: I don't know how to save the output of "system("ping")" in a variable so I can display it, or how to get the IP to ping from the user (can't figure out how to put in an input box)

---

### Post by Some Penguin on 2010-06-29
Have a look at 'popen'.

```

DESCRIPTION
       The  popen()  function  opens a process by creating a pipe, forking, and invoking the shell.  Since a pipe is by definition unidirectional, the type argument may specify only reading or writing, not both; the
       resulting stream is correspondingly read-only or write-only.

       The command argument is a pointer to a null-terminated string containing a shell command line.  This command is passed to /bin/sh using the -c flag; interpretation, if any, is performed  by  the  shell.   The
       type argument is a pointer to a null-terminated string which must be either "r" for reading or "w" for writing.

The  return  value  from  popen() is a normal standard I/O stream in all respects save that it must be closed with pclose() rather than fclose(3).  Writing to such a stream writes to the standard input of the
       command; the command&#8217;s standard output is the same as that of the process that called popen(), unless this is altered by the command itself.  Conversely, reading from a "popened" stream  reads  the  command&#8217;s
       standard output, and the command&#8217;s standard input is the same as that of the process that called popen().

```

---

### Post by ibuclaw on 2010-06-29
Or do it the GTK/GLib way with g_spawn_* ()

[http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html](http://library.gnome.org/devel/glib/unstable/glib-Spawning-Processes.html)

Regards

---

### Post by Crazedpsyc on 2010-06-29
> **Some Penguin said:**
> Have a look at 'popen'.

That sounds useful, could you tell me how to use it?
here's my code (still very early development obviously):
```

#include <stdlib.h>
#include <gtk/gtk.h>
#include <sys/types.h>
#include <stdio.h>
#include <unistd.h>
static void ping (GtkWidget *wid, GtkWidget *win)
{
  GtkWidget *dialog = NULL;
  GtkWidget *dialog2 = NULL;
  GtkWidget *pingy;
  GtkWidget *button;
  gtk_window_set_title (GTK_WINDOW (dialog), "Snoopy - Ping");
  gtk_window_set_position (GTK_WINDOW (dialog), GTK_WIN_POS_CENTER);
  dialog = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_OK, "Please inter a valid IP address or hostname");
      gtk_button_new_with_label ("Go!");
  gtk_dialog_run (GTK_DIALOG (dialog));
  pingy = system("ping -c 10 -s 24 127.0.0.1");
  gtk_widget_destroy (dialog);
  dialog2 = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_CLOSE, "Output:" < pingy);
  gtk_dialog_run (GTK_DIALOG (dialog2));
  gtk_widget_destroy (dialog2);
}
static void traceroute (GtkWidget *wid, GtkWidget *win)
{
  GtkWidget *dialog = NULL;
  GtkWidget *dialog2 = NULL;
  GtkWidget *tracey = NULL;
  dialog = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_OK, "Please inter a valid IP address or hostname");

  gtk_window_set_title (GTK_WINDOW (dialog), "Snoopy - Traceroute");
  gtk_window_set_position (GTK_WINDOW (dialog), GTK_WIN_POS_CENTER);
  gtk_dialog_run (GTK_DIALOG (dialog));
  tracey = system("traceroute 127.0.0.1");
  dialog2 = gtk_message_dialog_new (GTK_WINDOW (win), GTK_DIALOG_MODAL, GTK_MESSAGE_INFO, GTK_BUTTONS_CLOSE, "tracey");
  gtk_dialog_run (GTK_DIALOG (dialog2));
  gtk_widget_destroy (dialog2);
  gtk_widget_destroy (dialog);
}
int main (int argc, char *argv[])
{
  GtkWidget *button = NULL;
  GtkWidget *win = NULL;
  GtkWidget *vbox = NULL;

  /* Initialize GTK+ */
  g_log_set_handler ("Gtk", G_LOG_LEVEL_WARNING, (GLogFunc) gtk_false, NULL);
  gtk_init (&argc, &argv);
  g_log_set_handler ("Gtk", G_LOG_LEVEL_WARNING, g_log_default_handler, NULL);

  /* Create the main window */
  win = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_container_set_border_width (GTK_CONTAINER (win), 8);
  gtk_window_set_title (GTK_WINDOW (win), "Snoopy");
  gtk_window_set_position (GTK_WINDOW (win), GTK_WIN_POS_CENTER);
  gtk_widget_realize (win);
  g_signal_connect (win, "destroy", gtk_main_quit, NULL);

  /* Create a vertical box with buttons */
  vbox = gtk_vbox_new (TRUE, 6);
  gtk_container_add (GTK_CONTAINER (win), vbox);

  button = gtk_button_new_with_label ("Ping");
  g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK (ping), (gpointer) win);
  gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 0);

  button = gtk_button_new_from_stock (GTK_STOCK_DIALOG_INFO);
  g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK (traceroute), (gpointer) win);
  gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 0);

  button = gtk_button_new_from_stock (GTK_STOCK_CLOSE);
  g_signal_connect (button, "clicked", gtk_main_quit, NULL);
  gtk_box_pack_start (GTK_BOX (vbox), button, TRUE, TRUE, 0);
  /* Enter the main loop */
  gtk_widget_show_all (win);
  gtk_main ();
  return 0;
}


```

---

### Post by ibuclaw on 2010-06-29
Just throwing in the g_spawn usage:
```

#include <stdio.h>
#include <glib.h>

int main()
{
    GError* error = NULL;
    gchar *ioout, *ioerr;
    gint exit_status;

    g_spawn_command_line_sync("traceroute 127.0.0.1", &ioout, &ioerr, &exit_status, &error);

    if(!exit_status) {
        // Success, stdout is in ioout
        printf("%s\n", ioout);
    }
    else {
        printf("%s\n", error->message);
    }

    return 0;
}

```
Should be enough to get your feet moving...

To compile, you can use pkg-config:
```
gcc test.c `pkg-config --cflags --libs glib-2.0`
```

---

### Post by nvteighen on 2010-06-30
Hm... I'd rather use popen()... That g_spawn_command_line_sync() makes it easy for you to leak memory because it asks you to free that memory manually... (using g_free).

---

### Post by Crazedpsyc on 2010-06-30
Wow thanks for the quick answers! But please help get an input box into that initial "Please enter a valid IP address or hostname" screen and then how to use the User's input for the IP or host. It sounds soooo easy, but this is my first app ever. (except in javascript and that doesn't count)

ALSO::: Be aware that I have Codeblocks IDE, so it takes care of all that compiling stuff for me ;-))

AND ALSO::: How do I make a button have a popup description (like in html when you use <button title="Description">Button</button>)

---

### Post by nvteighen on 2010-07-01
> **Crazedpsyc said:**
> 
AND ALSO::: How do I make a button have a popup description (like in html when you use <button title="Description">Button</button>)

As far as I know, GTK+ allows that for toolbox buttons, not regular ones. But I may be wrong.

---

### Post by Crazedpsyc on 2010-07-01
What does that mean? I can find no references to "toolbox buttons" in the e-copy of "The Official GNOME 2 Developer's Guide"

---

### Post by nvteighen on 2010-07-02
> **Crazedpsyc said:**
> What does that mean? I can find no references to "toolbox buttons" in the e-copy of "The Official GNOME 2 Developer's Guide"

Why don't you use the API docs? It's usually much better to use those, seriously.

Do the following:
```

sudo apt-get install devhelp libgtk2.0-doc

```

And then in GNOME, use Applications->Programming->DevHelp (or execute devhelp from an X terminal).

---

### Post by Crazedpsyc on 2010-07-03
Thanks! Devhelp looks great!

---

### Post by StephenF on 2010-07-03
For "pop-up descriptions":
[http://library.gnome.org/devel/gtk/stable/GtkTooltip.html](http://library.gnome.org/devel/gtk/stable/GtkTooltip.html)

---

### Post by Crazedpsyc on 2010-07-05
thanks that link is very useful! I know this can be done, but I can find no reference to it in devhelp. How do i put a whaddeveryacallit [shell, terminal, console, konsole, bash, etc] in a GTK+ window?
and also how can I get a variable from one function to another? I want to get the value from
```

static void enter_callback( GtkWidget *widget,
                            GtkWidget *entry )
{
  const gchar *entry_text;
  entry_text = gtk_entry_get_text (GTK_ENTRY (entry));
}

```
to a to the  g_spawn_command_line_sync thing, but how can I do that when, not only is it in a separate function, but I have no idea how to run traceroute whatevertheywant. is there something like the javascript '"text" + variable' that I can do?

---

