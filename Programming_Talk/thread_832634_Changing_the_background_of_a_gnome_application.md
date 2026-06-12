---
title: "Changing the background of a gnome application"
date: 2008-06-17
forum: Programming Talk
---

### Post by lorderico on 2008-06-17
I tried to create a simple gnome program that would change the color of the background.  I found two ways to change color.  One is for gtk 1.2 (commented out), the other for gtk 2+.  I get the error:

myapp.c:(.text+0x251): undefined reference to `gtk_widget_modify_bg'
collect2: ld returned 1 exit status

Do you know why this is happening?   

/* A sample GNOME program
Created By: Eric Kulcyk
Date: 16th June, 2008
*/

#include <gnome.h>
#include <gtk/gtk.h>

static void enter_pressed(GtkWidget *button, GtkWidget *entry[])//gpointer data)
{
//GtkWidget *text_entry = data;
char *logon_string = gtk_entry_get_text(GTK_ENTRY(entry[0]));
char *password_string = gtk_entry_get_text(GTK_ENTRY(entry[1]));
g_print("\nLogon: %s\nPassword: %s\n",logon_string,password_string);
}

int main(int argc, char *argv[])
{
GtkWidget *app;
GtkWidget *label1, *label2;
GtkWidget *vbox, *entry[2];
GtkWidget *button;

gnome_init("example", "0.1", argc, argv);
app = gnome_app_new("example", "Login");
gtk_container_border_width(GTK_CONTAINER(app), 5);

vbox = gtk_vbox_new(FALSE, 0);

button = gtk_button_new_with_label("Logon");

/* we now create a Label: */
label1 = gtk_label_new("Username: ");
label2 = gtk_label_new("Password: ");

gtk_misc_set_alignment(GTK_MISC(label1), 0, 1.0);
gtk_misc_set_alignment(GTK_MISC(label2), 0, 1.0);

entry[0] = gtk_entry_new();
gtk_entry_set_visibility(GTK_ENTRY(entry[0]), TRUE);

entry[1] = gtk_entry_new();
gtk_entry_set_visibility(GTK_ENTRY(entry[1]), FALSE);

  GdkColor color;

  gdk_color_parse ("red", &color);

  gtk_widget_modify_bg (app, GTK_STATE_NORMAL, &color);<--This part doesn't work

//GtkRcStyle *rc_style;
  //GdkColor color;

  /* There are two good ways to fill in a color */

  /* 1) Initialize r/g/b components, they are 16-bit values */
  //color.red = 65535;
  //color.green = 0;
  //color.blue = 0;

  /* 2) Parse a color string; an HTML color spec such as "#FF0000"
   * is allowed here too
   */
  //gdk_color_parse ("red", &color);


  /* After filling in your GdkColor, create a GtkRcStyle */

  //rc_style = gtk_rc_style_new ();

  /* Set foreground (fg) color in normal state to red */
  //rc_style->fg[GTK_STATE_NORMAL] = color;

  /* Indicate which colors the GtkRcStyle will affect; 
   * unflagged colors will follow the theme
   */
  //rc_style->color_flags[GTK_STATE_NORMAL] |= GTK_RC_FG;

  //gtk_widget_modify_style (app, rc_style);

  //gtk_rc_style_unref (rc_style);


gtk_box_pack_start(GTK_BOX(vbox), label1, FALSE, FALSE, 0);
gtk_box_pack_start(GTK_BOX(vbox), entry[0], FALSE, FALSE, 0);
gtk_box_pack_start(GTK_BOX(vbox), label2, FALSE, FALSE, 0);
gtk_box_pack_start(GTK_BOX(vbox), entry[1], FALSE, FALSE, 0);
gtk_box_pack_start (GTK_BOX(vbox), button, FALSE, FALSE, 0);

gtk_signal_connect (GTK_OBJECT (button), "clicked",GTK_SIGNAL_FUNC (enter_pressed),entry);
gtk_signal_connect(GTK_OBJECT(app), "delete_event", GTK_SIGNAL_FUNC(gtk_main_quit), NULL);
//gtk_signal_connect(GTK_OBJECT(entry[0]), "activate", GTK_SIGNAL_FUNC(enter_pressed), entry);
//gtk_signal_connect(GTK_OBJECT(entry[1]), "activate", GTK_SIGNAL_FUNC(enter_pressed), entry);

gnome_app_set_contents(GNOME_APP(app), vbox);
gtk_widget_show_all(app);
gtk_main( );
return 0;
}


Also, I am just getting into gui programming in linux.  What is the best thing to learn?  Should I be trying this, or using something like Glade Interface Designer?

Thanks, Eric

---

### Post by galileon on 2008-06-18
hi, im not familliar with programming with gtk myself, but 

undefined reference

usually means you are not linking against a library that you invoked in your program...

there's probably a switch you need to add to your gcc/g++ commandline, eg

gcc program.c -lgtk

where the -l (small L), means link against this library


hope this helps you to narrow it down

---

### Post by Vadi on 2008-06-18
What are the arguments you're compiling the program with?

And yes, learn Glade and use it. It's a great way to design a GUI - an excellent tutorial is available here ([click]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")).

---

### Post by Vadi on 2008-06-18
Edited: forums bugged out.

---

### Post by lorderico on 2008-06-19
gcc myapp.c -o myapp `gnome-config --cflags --libs gnomeui`

That is what I use to compile.  It is from this tutorial:
[http://linuxgazette.net/issue70/ghosh2.html](http://linuxgazette.net/issue70/ghosh2.html)

---

### Post by Vadi on 2008-06-20
That article is 7 years old... you use pkg-config instead of gnome-config now and use gtk2.0+ instead of gnomeui, I think. Look at the micah carrick tutorial.

---

### Post by lorderico on 2008-06-22
The tutorial looks great, thanks for the suggestion.

---

