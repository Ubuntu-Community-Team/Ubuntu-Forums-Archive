---
title: "progamming/gtk havoc"
date: 2007-07-22
forum: Programming Talk
---

### Post by t3hi3x on 2007-07-22
welp, im a software developer. i know visual basic very well i think its time to start expanding. i am starting a company and we need to write software for a client machine, and we hate windows so its time to learn c++

i'm doing good with the basics. not problems. made a few simple apps, but i dont want to keep making useless crap. here is my deal. i am using the IDE in gnome called Anjuta, which basically is just an editor with the ability to access g++ within it...neat.

i found a tutorial online that is helping me with gtk+. i'm liking what im reading. i go to compile this hello world application:

```
* example-start helloworld helloworld.c */

#include <gtk/gtk.h>

/* this is a callback function. the data arguments are ignored in
 * this example.. More on callbacks below. */
void
hello (GtkWidget *widget, gpointer data)
{
        g_print ("Hello World\n");
}

gboolean
delete_event(GtkWidget *widget, GdkEvent *event, gpointer data)
{
        g_print ("delete event occurred\n");
        /* if you return FALSE in the "delete_event" signal
         * handler, GTK will emit the "destroy" signal.
         * Returning TRUE means you don't want the window
         * to be destroyed. This is useful for popping up
         * 'are you sure you want to quit ?' type dialogs. */

        /* Change TRUE to FALSE and the main window will
         * be destroyed with a "delete_event". */

        return TRUE;
}

/* another callback */
void
destroy (GtkWidget *widget, gpointer data)
{
        gtk_main_quit ();
}

int
main (int argc, char *argv[])
{
        /* GtkWidget is the storage type for widgets */
        GtkWidget *window;
        GtkWidget *button;

        /* this is called in all GTK applications.
         * arguments are parsed from the command line and
         * are returned to the application. */
        gtk_init (&argc, &argv);

        /* create a new window */
        window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

        /* when the window is given the "delete_event" signal
         * (this is given by the window manager, usually by
         * the 'close' option, or on the titlebar), we ask
         * it to call the delete_event () function as defined
         * above.  The data passed to the callback function
         * is NULL and is ignored in the callback function. */
        gtk_signal_connect (GTK_OBJECT (window), "delete_event",
                            GTK_SIGNAL_FUNC (delete_event), NULL);

        /* here we connect the "destroy" event to a signal
         * handler. This event occurs when we call
         * gtk_widget_destroy() on the window, or if we
         * return 'FALSE' in the "delete_event" callback. */
        gtk_signal_connect (GTK_OBJECT (window), "destroy",
                            GTK_SIGNAL_FUNC (destroy), NULL);

        /* sets the border width of the window. */
        gtk_container_border_width (GTK_CONTAINER (window), 10);

        /* creates a new button with the label "Hello World". */
        button = gtk_button_new_with_label ("Hello World");

        /* When the button receives the "clicked" signal, it
         * will call the function hello() passing it NULL as
         * it's argument.  The hello() function is defined
         * above. */
        gtk_signal_connect (GTK_OBJECT (button), "clicked",
                            GTK_SIGNAL_FUNC (hello), NULL);

        /* This will cause the window to be destroyed by
         * calling gtk_widget_destroy(window) when "clicked".
         * Again, the destroy signal could come from here,
         * or the window manager. */
        gtk_signal_connect_object (GTK_OBJECT (button), "clicked",
                                   GTK_SIGNAL_FUNC (gtk_widget_destroy),
                                   GTK_OBJECT (window));

        /* this packs the button into the window
         * (a gtk container). */
        gtk_container_add (GTK_CONTAINER (window), button);

        /* the final step is to display this newly created
         * widget... */
        gtk_widget_show (button);

        /* and the window */
        gtk_widget_show (window);

        /* all GTK applications must have a gtk_main().
         * Control ends here and waits for an event to occur
         * (like a key press or mouse event). */
        gtk_main ();

        return 0;
}
/* example-end */
```

i keep getting gay redirection errors on the header files: gtk/gtk.h

saying it cant find the header files

so im like ok..ill just search for the files and theyre in /lib/include/bla bla bla

i add the location to the includes and i get crap from the includes with in gtk.h and glib.h. so i said eff it and went to forums wondering how in the world to make sure i have to correct file redirection on the files. i went to the terminal and i type:

```
apbresh@uranus:/usr/lib/gtk$ whereis glib
glib: /usr/lib/glib
apbresh@uranus:/usr/lib/gtk$ whereis glib.h
glib: /usr/lib/glib
apbresh@uranus:/usr/lib/gtk$ whereis glib/glib.h
glib: /usr/lib/glib
apbresh@uranus:/usr/lib/gtk$ 

```

and guess what. there are no header files in this location.

im a n00b to c++ and a mid level linux user. i know a lot about some things, but others especially program devel i dont know what the heck im talking about.

let me know if you have questions or comments.

---

### Post by olejorgen on 2007-07-22
You need to install the development packages.
I think it's libgtk2.0-dev fro the c version and libgtkmm2.0-dev for the c++ bindings, but do a search in synaptic for libgtk to be sure.

> 
welp, im a software developer. i know visual basic very well i think its time to start expanding. i am starting a company and we need to write software for a client machine, and we hate windows so its time to learn c++
That did not make much sense :) "I hate windows" does not imply that you have to use c++ ^^

---

### Post by niteshifter on 2007-07-23
> That did not make much sense  "I hate windows" does not imply that you have to use c++ ^^

Oh it did to me! I gathered from the OP that he's been a VB programmer. Like I used to be. When one gets a belly full of Microsoft and leaves the dark side ... over here in GNU/Linux land BASIC is pretty much non-existent as a language, there is very little available  - anywhere - for the sophisticated tools like debug, GUI toolkits, and IDE, etc. C and C++ are encountered frequently and one certainly has choices for tools .... so yes, for some programmers leaving windows means learning C/C++ or another "robust" OOP language (native VB was rather weak at this).

Mind you, I'm not complaining and nor do I really miss VB work or any other aspect of Windows-land. But I'll always have a fond spot for BASIC - it was the first computer language I learned in high school - Dartmouth BASIC, via the local college IBM 360. Code submitted using punched cards.

Yes, I've been at this programming thing a long time ;)

---

### Post by t3hi3x on 2007-07-23
here's some output files: the fist being the output when i compile it:

```
apbresh@uranus:~/programming_072107$ g++ gtkexample.cc -o gtkexample
gtkexample.cc:5:21: error: gtk/gtk.h: No such file or directory
gtkexample.cc:6:21: error: glib/glib: No such file or directory
gtkexample.cc:9: error: ‘gint’ does not name a type
gtkexample.cc:17: error: variable or field ‘button_clicked’ declared void
gtkexample.cc:17: error: ‘GtkWidget’ was not declared in this scope
gtkexample.cc:17: error: ‘widget’ was not declared in this scope
gtkexample.cc:17: error: ‘gpointer’ was not declared in this scope
gtkexample.cc:17: error: initializer expression list treated as compound expression
gtkexample.cc:18: error: expected ‘,’ or ‘;’ before ‘{’ token
gtkexample.cc: In function ‘int main(int, char**)’:
gtkexample.cc:25: error: ‘GtkWidget’ was not declared in this scope
gtkexample.cc:25: error: ‘window’ was not declared in this scope
gtkexample.cc:26: error: ‘button’ was not declared in this scope
gtkexample.cc:29: error: ‘gtk_init’ was not declared in this scope
gtkexample.cc:32: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
gtkexample.cc:32: error: ‘gtk_window_new’ was not declared in this scope
gtkexample.cc:35: error: ‘gtk_button_new_with_label’ was not declared in this scope
gtkexample.cc:38: error: ‘GTK_OBJECT’ was not declared in this scope
gtkexample.cc:38: error: ‘destroyapp’ was not declared in this scope
gtkexample.cc:38: error: ‘GTK_SIGNAL_FUNC’ was not declared in this scope
gtkexample.cc:38: error: ‘NULL’ was not declared in this scope
gtkexample.cc:38: error: ‘gtk_signal_connect’ was not declared in this scope
gtkexample.cc:44: error: ‘GTK_CONTAINER’ was not declared in this scope
gtkexample.cc:44: error: ‘gtk_container_add’ was not declared in this scope
gtkexample.cc:47: error: ‘gtk_container_border_width’ was not declared in this scope
gtkexample.cc:50: error: ‘gtk_widget_show’ was not declared in this scope
gtkexample.cc:54: error: ‘gtk_main’ was not declared in this scope

```

lol love the errors

i did install all the libgtk*-dev libs and the ones you spoke of. the regular libgtk2-dev was installed, but i did install the second and still is giving me the redirection error. in fact i instantly thought when i got this error that i should install the packages. is there any tests i can do? i know all of those .h files are in /usr/include/gtk2.0 and /usr/include/glib.

this is all driving me crazy.

also about the vb thing. i love vb. yea its horrible inefficient and made by the devil, but it is very easy to work especially for beginning programmers that are nervous at the sight of code like c++.

and i guess basic would be my first language back in junior high, but that wasnt but vb6. and i still love how easy it is, but its not real programming. the reason i chose c++ is that i need to know it. its the most commonly accepted language in the world, plus i can port a program made in c++ to just about any os with out much re coding....plus its efficient, and there are tons of IDEs and tutorials online. and if you can suggest any thing of this sort let me know was well.

me an another programmer actually have the client software we were going to use for our product written in VB...and we're porting it to linux to cut the cost of running windows, as it is $150 for a copy of xp, and MS doesnt allow buying a VLK without currently having one....ms truly is the devil. ](*,) and thus we are completely converting to linux....its just a good idea period. i hate m$ more and more as the days move on.....lol we had a fight with them about vista too, but thats another story for another day

i have like every dev gtk package and glib package i can see so let me have it!

---

### Post by Wybiral on 2007-07-23
How does the compiler know to include the GTK libs? You need to tell it...

```

gcc gtkexample.c -o gtkexample `pkg-config --cflags --libs gtk+-2.0`

```

In this case I used pkg-config because it does all the work for me (of setting up the compiler flags).

Try this from the command line alone:

```

pkg-config --cflags --libs gtk+-2.0

```

See all that crap it outputs? Those are the libraries and paths required for compiling a GTK app, your compiler has to know what to include.

---

