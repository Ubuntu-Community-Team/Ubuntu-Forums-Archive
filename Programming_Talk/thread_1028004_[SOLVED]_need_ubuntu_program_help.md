---
title: "[SOLVED] need ubuntu program help"
date: 2009-01-01
forum: Programming Talk
---

### Post by reldon on 2009-01-01
Help !!  

I wrote a program using glade tutorials that works and am trying to get it to run with a launcher.  I checked the path variables and put the files into the usr/games directory thinking that would work.

I have the following files:

garden : the executable
Garden.glade : the glade file for the window the program uses
Off.jpg : the Off image file used by the window/program
On.jpg : the On image file used by the window/program

I verified each file has the following permissions: -rwxr-xr-x

I created a launcher by dragging the executable to the panel. This created a link which included the full path.

When I click on the launcher the display (launcher icon) shows some kind of animation (like it expands then disappears) but the program does not run. If I go to the directory where it is (ie usr/games) and double click on the garden executable then it runs fine.

It will also run from the usr/games directory if I am using my regular login or as sudo in nautilus.

I am totally stumped and confused.

Are suggestions as to why I this won't work?
:confused:

---

### Post by slavik on 2009-01-01
try running it from command line, maybe you'll get an error that would tell us what is wrong.

I would double check the paths of files, just in case.

---

### Post by reldon on 2009-01-02
I launched a terminal window, changed to the /usr/games directory, typed garden then enter and it ran fine.  this was done using my normal login, not as sudo..

the launcher has the full path and filename (ie.  /usr/games/garden)

????

---

### Post by reldon on 2009-01-02
here is my path string.

rel@dell-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
rel@dell-desktop:~$

---

### Post by slavik on 2009-01-02
hmm ... how did you code the paths to the glade and other files in your program? if you used a relative path, that could explain why it wouldn't work from a launcher.

---

### Post by reldon on 2009-01-02
As you might know by now I am a consumate novice to the linux programming world.  ;-)

Here is the source I used to make the executable.  I used the glade3 to make the main window.



/*
 * Garden.cc
 *
 *
 * Use to compile
 * g++ -Wall -c `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0` -o garden Garden.c
 *
 *
 *
 *
*/

#include <gtk/gtk.h>
#include <glib.h>
#include <glade/glade.h>
#include <time.h>

#include <asm/types.h>
#include <stdbool.h>
#include "pmd.h"
#include "usb-1024LS.h"

#define GLADE_FILE "Garden.glade"

//using namespace std;

struct window
{
	GladeXML		*sgxml;
	GtkWidget	*swindow;
	GtkWidget	*sentry;
	GtkWidget	*simage;
} Main, *mainPtr;

gboolean
time_handler (gpointer data)
{
	/* Get the current time. */
	time_t curtime = time (NULL);
	if(curtime % 2 ){
		gtk_image_set_from_file(GTK_IMAGE(Main.simage), "On.jpg");
		gtk_entry_set_text(GTK_ENTRY(Main.sentry), "Timeout On!");
	}
	else{
		gtk_image_set_from_file(GTK_IMAGE(Main.simage), "Off.jpg");
		gtk_entry_set_text(GTK_ENTRY(Main.sentry), "Timeout Off!");
	}
	
return TRUE;
}

void 
on_button1_clicked (GtkButton *button, gpointer data)
{
   /* set the entry's text */
   gtk_entry_set_text (GTK_ENTRY(Main.sentry), "Hello World!");
   gtk_image_set_from_file (GTK_IMAGE(Main.simage), "On.jpg");
}

int
main (int argc, char *argv[])
{
    GladeXML 	*gxml = NULL;
    GtkWidget	*window = NULL;
    GtkWidget	*entry = NULL;
    GtkWidget	*image = NULL;
    
    /* initialize GTK+ libraries */
    gtk_init (&argc, &argv);

    /* build main window from Glade XML file */
    gxml = glade_xml_new (GLADE_FILE, NULL, NULL);
    g_assert (gxml);
	    
    /* get widgets from Glade XML file */
    window = glade_xml_get_widget (gxml, "main");
    entry = glade_xml_get_widget (gxml, "entry1");
    image = glade_xml_get_widget (gxml, "image1");

    /* Set up pointers for structure */
    mainPtr = &Main;
    Main.sgxml = gxml;
    Main.swindow = window;
    Main.sentry = entry;
    Main.simage = image;
   
    /* call gtk_main_quit() when the window's "x" is clicked */
    glade_xml_signal_connect (gxml, "on_main_destroy",
            G_CALLBACK (gtk_main_quit));
   
    /* call on_button1_clicked() when button1 is clicked, passing the text
    entry widget to the function as the user_data */
    glade_xml_signal_connect_data (gxml, "on_button1_clicked",
            G_CALLBACK (on_button1_clicked), mainPtr);
   
   /* Add a timeout to update the heartbeat every 250 milliseconds or so */
	gboolean func_ref = g_timeout_add (250, time_handler, window);

   /* free Glade XML object */
   g_object_unref (G_OBJECT (gxml));

    /* begin GTK+ main loop */                   
    gtk_main();

   /* Remove the timeout function--not that it matters since we're about to end */
  g_source_remove (func_ref);

return 0;
}

---

### Post by reldon on 2009-01-02
please note also that the original filename was changed from Garden.cc to garden.c

And lastly, how do I thank you in this forum for your help??

:P

---

### Post by slavik on 2009-01-02
you're using relative paths in your program, try replacing them with full paths :)

---

### Post by reldon on 2009-01-02
You are the man !!!

I didn't understand at first what you meant by putting the full path in the source code.  Then it dawned on me..!!!

I added the full path to the glade file and both image files and viola!! it runs perfect...

Thanks so much for your great help..  This also gives me some insight on how finicky linux is..  !!  

Happy new year to you and thanks a bunch...

---

