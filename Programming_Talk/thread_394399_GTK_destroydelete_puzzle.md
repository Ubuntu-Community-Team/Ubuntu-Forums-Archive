---
title: "GTK destroy/delete puzzle"
date: 2007-03-26
forum: Programming Talk
---

### Post by rebelxt on 2007-03-26
I have a fairly simple program, the proper termination of which has me baffled.  I am trying to write a reusable GUI dialog using GTK2 as an exercise in learning to write that type of program.

The main program generates a window with Click, Quit, and Close (X) buttons.  The Quit and Close buttons should terminate this window.  The Click button causes a second window to be generated with Yes, No, and Close (X) buttons.  The Click button can be clicked as many times as required/desired.  The Yes, No, and Close buttons should all terminate this window.

What I can't figure out is the proper coding of the "delete_event" and "destroy" signals to terminate each of these windows.  The following program has some user functions and print statements that were included to try to find something that would work.

Can anyone help me?
rebelxt

```
/* yesno.c - A simple program with a reusable dialog. */



#include <gtk/gtk.h>

#include <string.h>



int yes_no_dialog (gchar *title, gchar *labeltext);

static void yesno_func (GtkWidget *widget, gchar *yesno);

static void button_func (GtkWidget *widget, gpointer pdata);

static gint Mdelete_func (GtkWidget *widget, gpointer data);

static gint Ydelete_func (GtkWidget *widget, gpointer data);



/* A static variable for the yes/no return value. */

static gint yesno=-1;



/*  Test the delete signal.  */

static gint Mdelete_func (GtkWidget *widget, gpointer data)

{

	g_print("Mdelete called by main\n");

	gtk_main_quit();

	return TRUE;

}



/*  Test the delete signal.  */

static gint Ydelete_func (GtkWidget *widget, gpointer data)

{

	g_print("Ydelete called by YesNo\n");

	gtk_main_quit();

	return TRUE;

}



int main(int argc, char *argv[])

{

	GtkWidget *window;

	GtkWidget *button, *qbutton, *box;



	gtk_init(&argc, &argv);

    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);



    g_signal_connect(G_OBJECT(window), "destroy",

                G_CALLBACK(gtk_main_quit), NULL);

    g_signal_connect(G_OBJECT(window), "destroy",

                G_CALLBACK(gtk_main_quit), NULL);

    g_signal_connect(G_OBJECT(window), "delete_event",

                G_CALLBACK(Mdelete_func), "main");



	gtk_container_set_border_width(GTK_CONTAINER(window), 20);

	

/*    gtk_widget_set_usize(GTK_WIDGET(window), 280, 100);

*/

    gtk_window_set_title(GTK_WINDOW(window), "GTK Test");

	box = gtk_hbox_new(FALSE, 20);

	gtk_container_add(GTK_CONTAINER(window), box);



	/*  Set up a button.  */

    button = gtk_button_new_with_label(" Click to demonstrate \n     the YesNo dialog ");

    g_signal_connect(G_OBJECT(button), "clicked",

                G_CALLBACK(button_func), NULL);

	gtk_box_pack_start(GTK_BOX(box), button, TRUE, FALSE, 0);



	/*  Set up the second button.  */

    qbutton = gtk_button_new_with_label("   Quit   ");

    g_signal_connect(G_OBJECT(qbutton), "clicked",

                G_CALLBACK(gtk_main_quit), NULL);

	gtk_box_pack_end(GTK_BOX(box), qbutton, TRUE, FALSE, 0);



	/*  Make the window visible.  */

	gtk_widget_show_all(window);

	gtk_main();



	return 0;

}



static void button_func (GtkWidget *widget, gpointer pdata)

{

	g_print("Ready to call the yes_no_dialog.\n");

	g_printf("The return value is currently %d\n", yes_no_dialog("YesNo", "Yes returns TRUE (1).\nNo returns FALSE (0)."));

}



/* yesno.c - a general purpose yes/no dialog. */



    GtkWidget *dialog;

int yes_no_dialog (gchar *title, gchar *labeltext)

{    

    GtkWidget *label, *ybutton, *nbutton;

    GtkWidget *vbox, *hbox;

	int tlgt, height, width;

	int n, i, max, lines=1;



	/* Calculate the required width. */

	width = strlen(title) * 9 + 110;	/* space for title */

	if (width < 125)  width = 125;

	max = 0;

	for (n=0, i=0; labeltext[n]; n++, i++)

	{

		if (labeltext[n] == '\n')

		{

			lines++;

			if (i > max)  max = i;

			i = 0;

		}

	}

	if (i> max)  max = i;

	tlgt = (max + 1) * 6.75;

	if (tlgt > width) width = tlgt;

	/* Calculate the required height. */

	height = lines * 16 + 40;



    /* Create the required widgets. */

    dialog  = gtk_window_new(GTK_WINDOW_TOPLEVEL);

    label   = gtk_label_new(labeltext);

    ybutton = gtk_button_new_with_label("   Yes   ");

    nbutton = gtk_button_new_with_label("   No    ");

    vbox    = gtk_vbox_new(FALSE, 0); 

    hbox    = gtk_hbox_new(FALSE, 0);



    /* Pack the widgets. */

    gtk_box_pack_start(GTK_BOX(vbox), label, TRUE, FALSE, 0);

    gtk_box_pack_start(GTK_BOX(hbox), ybutton, TRUE, FALSE, 0);

    gtk_box_pack_start(GTK_BOX(hbox), nbutton, TRUE, FALSE, 0);

    gtk_box_pack_start(GTK_BOX(vbox), hbox, TRUE, FALSE, 0);

    gtk_container_add(GTK_CONTAINER(dialog), vbox);

    

    gtk_widget_set_usize(GTK_WIDGET(dialog), width, height);

    gtk_window_set_title(GTK_WINDOW(dialog), title);

    gtk_window_set_modal(GTK_WINDOW(dialog), TRUE);

 

    /* Connect the signals. */

    g_signal_connect(GTK_OBJECT(ybutton), "clicked",

                G_CALLBACK(yesno_func), "Yes");

    g_signal_connect_swapped(GTK_OBJECT(ybutton), "clicked",

                G_CALLBACK(gtk_widget_destroy), G_OBJECT(dialog));

				

    g_signal_connect(GTK_OBJECT(nbutton),  "clicked",

                G_CALLBACK(yesno_func), "No");

    g_signal_connect_swapped(GTK_OBJECT(nbutton), "clicked",

                G_CALLBACK(gtk_widget_destroy), G_OBJECT(dialog));



    g_signal_connect(G_OBJECT(dialog), "destroy",

                G_CALLBACK(gtk_widget_destroy), G_OBJECT(dialog));



	g_signal_connect(G_OBJECT(dialog), "delete_event",

                G_CALLBACK(Ydelete_func), "YesNo");



/* Make everything visible. */

    gtk_widget_show_all(dialog);

	gtk_main();



    return yesno;

}



static void yesno_func (GtkWidget *widget, gchar *yesnostr)

{ 

    if (yesnostr [0] == 'Y')

        yesno = TRUE;

    else

        yesno = FALSE;

	g_printf("The %s button was clicked.\n", yesnostr);

}

```

---

### Post by thethawav on 2007-03-27
add a callback function to your program called kill or something like that
pass 2 arguments to your callback function (the widget hooked with the function and the widget 
you're going to destroy as second parameter).

ex. : 

void kill(GtkButton *qbutton, GtkWindow *window)
{
 gtk_widget_destroy(window);
 gtk_main_quit();
}

hook the button with your callback function like that:
g_signal_connect(G_OBJECT(qbutton), "clicked", G_CALLBACK(kill), (gpointer) window);

---

### Post by rebelxt on 2007-03-29
OK, thanks, that's got me closer.  What's still happening is that when the popup dialog window is closed with the X button, that window does not go away.  Click the X button again, and both windows disappear.  There are no error messages.

Here is another version of my program; it's a bit more simple.  Any more help, please?

```
/* main.c - A simple program with a reusable dialog. */

#include <gtk/gtk.h>
#include <glib/gprintf.h>
#include <string.h>

int yes_no_dialog (gchar *title, gchar *labeltext);
static void yesno_func (GtkWidget *widget, GtkWidget *window);
static void button_func (GtkWidget *widget, gpointer pdata);
static gint Mdelete_func (GtkWidget *widget, gpointer data);
static gint Ydelete_func (GtkWidget *widget, gpointer data);
void kill(GtkButton *qbutton, GtkWidget *window);

/* A static variable for the yes/no return value. */
static gint yesno=-1;

void kill(GtkButton *qbutton, GtkWidget *window)
{
	g_print("kill called by main does gtk_widget_destroy(window) and gtk_main_quit()\n");
	gtk_widget_destroy(window);
	gtk_main_quit();
}	

/*  Test the delete signal.  */
static gint Mdelete_func (GtkWidget *widget, gpointer data)
{
	g_print("delete_event from main does gtk_main_quit()\n");
	gtk_main_quit();
	return TRUE;
}

int main(int argc, char *argv[])
{
	GtkWidget *window;
	GtkWidget *button, *qbutton, *box;

	gtk_init(&argc, &argv);
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

    g_signal_connect(G_OBJECT(window), "delete_event",
                G_CALLBACK(Mdelete_func), NULL);

	gtk_container_set_border_width(GTK_CONTAINER(window), 20);
	
    gtk_window_set_title(GTK_WINDOW(window), "GTK Test");
	box = gtk_hbox_new(FALSE, 20);
	gtk_container_add(GTK_CONTAINER(window), box);

	/*  Set up a button.  */
    button = gtk_button_new_with_label(" Click to demonstrate \n     the YesNo dialog ");
    g_signal_connect(G_OBJECT(button), "clicked",
                G_CALLBACK(button_func), NULL);
	gtk_box_pack_start(GTK_BOX(box), button, TRUE, FALSE, 0);

	/*  Set up the second button.  */
    qbutton = gtk_button_new_with_label("   Quit   ");

	gtk_box_pack_end(GTK_BOX(box), qbutton, TRUE, FALSE, 0);

	g_signal_connect(G_OBJECT(qbutton), "clicked",
				G_CALLBACK(kill), G_OBJECT( window));
	/*  Make the window visible.  */
	gtk_widget_show_all(window);
	gtk_main();

	return 0;
}

static void button_func (GtkWidget *widget, gpointer pdata)
{
	g_print("Ready to call the yes_no_dialog.\n");
	g_printf("The return value is currently %d\n", yes_no_dialog("YesNo", "Yes returns TRUE (1).\n"));
}

/* yesno.c - a general purpose yes/no dialog. */

int yes_no_dialog (gchar *title, gchar *labeltext)
{
    GtkWidget *dialog;
    GtkWidget *label, *ybutton;
    GtkWidget *vbox;

    /* Create the required widgets. */
    dialog  = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    label   = gtk_label_new(labeltext);
    ybutton = gtk_button_new_with_label("   Yes   ");
    vbox    = gtk_vbox_new(FALSE, 0); 
	
    /* Pack the widgets. */
    gtk_box_pack_start(GTK_BOX(vbox), label, TRUE, FALSE, 0);
    gtk_box_pack_start(GTK_BOX(vbox), ybutton, TRUE, FALSE, 0);
	gtk_container_add(GTK_CONTAINER(dialog), vbox);
    
    gtk_widget_set_usize(GTK_WIDGET(dialog), 155, 72);
    gtk_window_set_title(GTK_WINDOW(dialog), title);
    gtk_window_set_modal(GTK_WINDOW(dialog), TRUE);
 
    /* Connect the signals. */
    g_signal_connect(GTK_OBJECT(ybutton), "clicked",
                G_CALLBACK(yesno_func), G_OBJECT(dialog));
	g_signal_connect(G_OBJECT(dialog), "delete_event",
                G_CALLBACK(Ydelete_func), NULL);
				
/* Make everything visible. */
    gtk_widget_show_all(dialog);
	gtk_main();

    return yesno;
}

static void yesno_func (GtkWidget *widget, GtkWidget *dialog)
{
    yesno = TRUE;
	g_print("The Yes button was clicked, does gtk_widget_destroy(dialog) and gtk_main_quit().\n");
	gtk_widget_destroy(dialog);
	gtk_main_quit();
}


/*  Test the delete signal.  */
static gint Ydelete_func (GtkWidget *widget, gpointer data)
{
	g_print("delete_event from YesNo does gtk_main_quit()\n");
	gtk_main_quit();
	return TRUE;
}
```

---

### Post by wdk on 2007-03-30
The entire problem can be solved by simply changing the return value in Ydelete_func to FALSE.

The tutorial on the gtk website explains that the value returned by the delete_event handler determines what the applications will do from there. Returning FALSE will emit a destroy signal, thus destroying the window. Returning TRUE allows you to keep the window and do other things with it.
In fact, you can achieve even more control over your window if you divide the "delete_event" and "destroy" signal handlers into two separate functions (kind of what you were after in your first program).

Thus you could also destroy the dialog like this:
```


static gint Ydelete_func (GtkWidget *widget, gpointer data)
{
	g_print("delete_event from YesNo does gtk_main_quit()\n");
	return FALSE;
}

static void dialog_destroy(GtkWidget *widget, gpointer data)
{
	gtk_main_quit();
}

```

Again, if you return TRUE, the dialog won't close. Splitting the signal handlers like this also solves the problem that clicking X twice in the dialog shuts down the entire program. That is happening because returning TRUE does not close the dialog, but the "delete_event" handler is stopping the nested gtk_main() calls one by one. Since by the time the dialog is opened you have two gtk_main loops, the first time X is clicked the second instance of gtk_main is closed (and apparently "nothing" happens). The second time you click X in the dialog, the first instance of gtk_main is shut down and so is the program.

It's probably not a bad idea to split up your Mdelete_func function in similar way.

Check out section 2.5 of the gtk tutorial for examples and explanations: 
[http://www.gtk.org/tutorial1.2/gtk_tut-2.html]("http://www.gtk.org/tutorial1.2/gtk_tut-2.html")

Happy Hacking!

---

### Post by rebelxt on 2007-03-30
That's the last piece of the puzzle.  Thanks a million.

I did know about that tutorial, and had read that section.  Maybe if I had read it two or three more times, the connection would have clicked.

Anyway, thanks again.

---

### Post by kgaipal on 2010-08-09
thnx guys, it solved my dilemma too...

---

