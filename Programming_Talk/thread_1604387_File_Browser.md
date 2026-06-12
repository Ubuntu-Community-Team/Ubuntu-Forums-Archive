---
title: "File Browser?"
date: 2010-10-24
forum: Programming Talk
---

### Post by roadkillguy on 2010-10-24
I'm writing a simple game in c++, and I've run into a road block.  How do I enable the user to choose a file without writing a file chooser myself?

I've seen programs like Gedit and such start up a file browser to load files.  Are they hard coded with gtk?  Or are they built in?  If they're built in, I would like to know what functions to call.

Thanks!

---

### Post by dv3500ea on 2010-10-24
The easiest way would be to open a pipe to ```
zenity --file-selection

```. See ```
man zenity
``` for information about its use.

---

### Post by moma on 2010-10-24
Yes, Gedit and such are GTK/GDK programs.

Install the "gtk2.0-examples" package and study the code samples. Please do this (in a [terminal window]("http://www.futuredesktop.org/maverick/images/picture-6a.png")):

Install compiler and GTK header files (the -dev package).
[COLOR="DarkGreen"]sudo apt-get install libgtk2.0-dev build-essential[/COLOR]

Install GTK+2.0 samples
[COLOR="DarkGreen"]apt-cache search gtk2.0-examples[/COLOR]
[COLOR="DarkGreen"]sudo apt-get install gtk2.0-examples[/COLOR]

It puts the files to /usr/share/doc/gtk2.0-examples/. Take a copy so you can compile and edit the files in your $HOME. Do this:

[COLOR="DarkGreen"]cd $HOME[/COLOR]
[COLOR="DarkGreen"]cp -fr /usr/share/doc/gtk2.0-examples/ .[/COLOR]  # note the .

Now unpack (gzip -d) and compile the samples. First cd to the examples directory.
[COLOR="DarkGreen"]cd gtk2.0-examples/examples/[/COLOR]

Copy and paste this long command to your terminal window (copy & paste all):

[COLOR="DarkGreen"]for d in $(ls); do  
 if [ -d "$d" ]; then 
     cd "$d"
     gzip -dfq *.gz
     touch config.h 
     make
     cd ..
 fi 
done[/COLOR]

Then test-run the samples in **$HOME/gtk2.0-examples/examples/**. 
Study the Makefile(s) so you learn how to compile a GTK program.
--------------------

Here is an additional example to show how to use the GtkFileChooser dialog to pick a file or folder.
Ref: [http://library.gnome.org/devel/gtk/unstable/GtkFileChooser.html](http://library.gnome.org/devel/gtk/unstable/GtkFileChooser.html)

Save the following code to  test1.c and compile with 
[COLOR="DarkGreen"]gcc $(pkg-config --cflags --libs gtk+-2.0) test1.c -o test1[/COLOR]
Run it 
[COLOR="DarkGreen"]./test1[/COLOR]

```
#include <stdlib.h>
#include <gtk/gtk.h>

/* gcc $(pkg-config --cflags --libs gtk+-2.0) test1.c -o test1 */

GtkWidget *g_window;

void get_file(GtkWidget *button, gpointer user_data)
{
    gchar *last_path = getenv("HOME");

    /* Put the result into this edit field */
    GtkWidget *edit_field = (GtkWidget*)user_data;

    /* Open file dialog. Allow any file type. */
    GtkWidget *dialog = gtk_file_chooser_dialog_new("Open/get file", GTK_WINDOW(g_window),
	                    GTK_FILE_CHOOSER_ACTION_OPEN,
	                    GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT, NULL);

    /* Allow multiple selection:
    gtk_file_chooser_set_select_multiple(GTK_FILE_CHOOSER(dialog), TRUE);
    */

    /* Be nice and land on the last visited folder (most of the users prefer this function) */
    gtk_file_chooser_set_current_folder(GTK_FILE_CHOOSER(dialog), last_path);

    gtk_widget_show_all(dialog);
    gint result = gtk_dialog_run(GTK_DIALOG(dialog));

    if (result == GTK_RESPONSE_ACCEPT)
    {
        /* Get all selected filenames:
         GSList *selected_filenames = gtk_file_chooser_get_filenames(GTK_FILE_CHOOSER(dialog));
        */

        /* Get the filename */
        gchar *filename = gtk_file_chooser_get_filename(GTK_FILE_CHOOSER(dialog));
        gtk_entry_set_text(GTK_ENTRY(edit_field), filename);
	g_free(filename);
    }

    /* Get rid of the dialog */
    gtk_widget_destroy(dialog);
}

void quit()
{
  gtk_main_quit();
}

int main(int argc, char *argv[]) {
    gtk_init(&argc, &argv);

    g_window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_widget_set_name(g_window, "Test get/open file");
    gtk_window_set_default_size(GTK_WINDOW(g_window), 400, 200);

    GtkWidget *vbox = gtk_vbox_new(FALSE, 0);
    gtk_container_add(GTK_CONTAINER(g_window), vbox);
    gtk_widget_show(vbox);

    g_signal_connect(g_window, "destroy", G_CALLBACK(quit), NULL);

    GtkWidget *button = gtk_button_new_with_label("Get file...");
    gtk_box_pack_start(GTK_BOX(vbox), button, FALSE, FALSE, 0);

    GtkWidget *edit_field = gtk_entry_new();
    gtk_widget_show(edit_field);
    gtk_box_pack_start(GTK_BOX(vbox), edit_field, FALSE, FALSE, 0);

    g_signal_connect(button, "clicked", G_CALLBACK(get_file), edit_field/*user_data*/);
    gtk_widget_show(button);
    gtk_widget_show(g_window);

    gtk_main ();

    return 0;
} 
```

[COLOR="Red"]BTW:[/COLOR] Creating GTK/Cairo/Clutter/etc. applications with JavaScript is a hot topic now.
Get known with Seed (Javascript interpreter) and GTK.
Please follow the links [in this posting...]("http://linux1.no/forum/viewtopic.php?p=2189406#p2189406")

[http://www.futuredesktop.org](http://www.futuredesktop.org)

---

### Post by roadkillguy on 2010-10-24
..Now, that's for c++ correct?

Will it work with OpenGL and SDL?

@dv3500ea

I tried those commands and they look awesome.  How do I do that in c++?

---

### Post by dwhitney67 on 2010-10-24
> **roadkillguy said:**
> I'm writing a simple game in c++, and I've run into a road block.  How do I enable the user to choose a file without writing a file chooser myself?

I've seen programs like Gedit and such start up a file browser to load files.  Are they hard coded with gtk?  Or are they built in?  If they're built in, I would like to know what functions to call.

Thanks!

Well, if you want to continue to keep the game app simple, then merely prompt the user for the path to the file they want to use.  You can verify the existence of the file using stat().

If you want to candy-coat your app with a GUI, then it ceases to be a "simple" app.  You are then left with the choice of using either GTK+, wxWidgets, or a handful of other GUI toolkits, including the venerable X-Motif.

Standard C++ does not offer any GUI capabilities.

P.S.  I've attached a small (incomplete) project that utilizes X-Motif.

---

### Post by roadkillguy on 2010-10-24
...Right.  What's the package for that called? (As in apt-get install) Is it cross-platform?

---

### Post by roadkillguy on 2010-10-24
Does anybody know where I can find a simple tutorial on gtkmm?  I've written gtk code in c before, but I'm wondering if it's close to the same.

---

### Post by Jonas thomas on 2010-10-24
> **roadkillguy said:**
> Does anybody know where I can find a simple tutorial on gtkmm?  I've written gtk code in c before, but I'm wondering if it's close to the same.

[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-helloworld.html]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-helloworld.html")

This isn't on gtkmm but I found it fun for games
[http://www.videotutorialsrock.com/index.php]("http://www.videotutorialsrock.com/index.php")

---

