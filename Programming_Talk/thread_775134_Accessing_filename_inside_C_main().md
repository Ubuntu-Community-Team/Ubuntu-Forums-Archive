---
title: "Accessing filename inside C main() ?"
date: 2008-04-29
forum: Programming Talk
---

### Post by ecs_pf5 on 2008-04-29
I compiled an example hello world in C / GTK & it runs ok on KDE in Kubuntu:

```

#include <gtk/gtk.h>
 
static void clickity (GtkWidget *widget, gpointer data)
{
    gtk_button_set_label (GTK_BUTTON (widget), "World!");
}
 
static void byebye (GtkWidget * widget, gpointer data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *button;
 
    gtk_init (&argc, &argv);
 
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window), "destroy",
                      G_CALLBACK (byebye), NULL);
    gtk_window_set_title (GTK_WINDOW (window), "Hello,");
    gtk_container_set_border_width (GTK_CONTAINER (window), 20);
    gtk_window_set_default_size (GTK_WINDOW (window), 300, 50);
 
    button = gtk_button_new_with_label ("Clickity!");
    g_signal_connect (G_OBJECT (button), "clicked",
                      G_CALLBACK (clickity), NULL);
 
    gtk_container_add (GTK_CONTAINER (window), button);
 
    gtk_widget_show (button);
    gtk_widget_show (window);
 
    gtk_main ();
 
    return 0;
}

```

I packaged the resulting executable into a .deb, which was set to install it into /usr/bin/ 

I set the .deb to also provide an icon for the compiled 'app'.

I then set up a file association with *.fpt files (chosen at random hoping it to be fairly unique for local testing purpose only) 

Now, if I make an empty file, fill it with some random bytes, and make the filename end in .fpt, it then takes on the hello world app's icon, and will launch the hello app.

My question is:

In the C code above, how would I access the .fpt file's byte-content? I was thinking I could use *<stdio.h>; *FILE* f; f=fopen("filename","*rb*")... but where would I get <filename>?

---

### Post by eldragon on 2008-04-29
> **ecs_pf5 said:**
> I compiled an example hello world in C / GTK & it runs ok on KDE in Kubuntu:

```

#include <gtk/gtk.h>
 
static void clickity (GtkWidget *widget, gpointer data)
{
    gtk_button_set_label (GTK_BUTTON (widget), "World!");
}
 
static void byebye (GtkWidget * widget, gpointer data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *button;
 
    gtk_init (&argc, &argv);
 
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window), "destroy",
                      G_CALLBACK (byebye), NULL);
    gtk_window_set_title (GTK_WINDOW (window), "Hello,");
    gtk_container_set_border_width (GTK_CONTAINER (window), 20);
    gtk_window_set_default_size (GTK_WINDOW (window), 300, 50);
 
    button = gtk_button_new_with_label ("Clickity!");
    g_signal_connect (G_OBJECT (button), "clicked",
                      G_CALLBACK (clickity), NULL);
 
    gtk_container_add (GTK_CONTAINER (window), button);
 
    gtk_widget_show (button);
    gtk_widget_show (window);
 
    gtk_main ();
 
    return 0;
}

```

I packaged the resulting executable into a .deb, which was set to install it into /usr/bin/ 

I set the .deb to also provide an icon for the compiled 'app'.

I then set up a file association with *.fpt files (chosen at random hoping it to be fairly unique for local testing purpose only) 

Now, if I make an empty file, fill it with some random bytes, and make the filename end in .fpt, it then takes on the hello world app's icon, and will launch the hello app.

My question is:

In the C code above, how would I access the .fpt file's byte-content? I was thinking I could use *<stdio.h>; *FILE* f; f=fopen("filename","*rb*")... but where would I get <filename>?


i dont know much about programming, but 
```
 
int main (int argc, char *argv[])

```
seems to be the place where the filename is going to be given

maybe test what argv has......if im not mistaken there is a function to parse argv called getoptlong()

hope i helped

---

### Post by Lux Perpetua on 2008-04-29
Good question. I wasn't sure when I opened your thread, but a few quick trials confirm that the name of the file is passed to the program as a command-line argument. I think it should be the only command-line argument unless the user decides to use a custom command, in which case anything goes, of course.

---

### Post by ecs_pf5 on 2008-04-29
Could be helpful - thanks :)

[http://linux.about.com/library/cmd/blcmdl3_getopt_long.htm](http://linux.about.com/library/cmd/blcmdl3_getopt_long.htm)

I came up with something very vague that will not work, to try and display the info in a little window

pseudocode:
```

    textwindow = gtk.TextView
    textbuffer = gtk.TextBuffer

    for( int i = 0; i < argc; i++ )
    {
        textbuffer.Text += "arg %d: %s\n", i, argv[i], "\n";
    }

    gtk_widget_show (button);
    gtk_widget_show (textwindow);
    gtk_widget_show (window);

```..so I'll try and put that together with your suggestion somehow.

I don't know much about programming either, just playing about & trying to learn :guitar:

[edit] Thanks Lux perpetua, fingers crossed then :)





[edit again]

well I'm making a right mess here. getting my pointers in a twist.. come back to it later.....

gtk text view:
[http://library.gnome.org/devel/gtk/unstable/GtkTextView.html#gtk-text-view-get-buffer](http://library.gnome.org/devel/gtk/unstable/GtkTextView.html#gtk-text-view-get-buffer)

```

#include <gtk/gtk.h>
 
static void clickity (GtkWidget *widget, gpointer data)
{
    gtk_button_set_label (GTK_BUTTON (widget), "World!");
}
 
static void byebye (GtkWidget * widget, gpointer data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *button;
    GtkWidget *textwindow;
    GtkWidget *textbuffer;
 
    gtk_init (&argc, &argv);
 
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window), "destroy",
                      G_CALLBACK (byebye), NULL);
    gtk_window_set_title (GTK_WINDOW (window), "Hello,");
    gtk_container_set_border_width (GTK_CONTAINER (window), 20);
    gtk_window_set_default_size (GTK_WINDOW (window), 500, 200);
 
    button = gtk_button_new_with_label ("Clickity!");
    g_signal_connect (G_OBJECT (button), "clicked",
                      G_CALLBACK (clickity), NULL);
 
    gtk_container_add (GTK_CONTAINER (window), button);


    textwindow = gtk_text_view_new ();
    gtk_text_view_set_border_window_size (GTK_TEXT_VIEW (textwindow), 50, 50);
    /* textbuffer = gtk_text_view_get_buffer (textwindow);

    int counter;

    for (counter=0; counter < argc; counter++)
        {
        textbuffer += argv[counter] + "\n";
        }
    */
    gtk_widget_show (textwindow);
    //gtk_widget_show (button);
    
    gtk_widget_show (window);
 
    gtk_main ();
 
    return 0;
}

```
[ ]("http://ubuntuforums.org/member.php?u=33455")

---

