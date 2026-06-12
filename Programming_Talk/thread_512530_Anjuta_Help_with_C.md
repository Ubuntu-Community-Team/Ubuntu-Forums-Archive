---
title: "Anjuta Help with C"
date: 2007-07-29
forum: Programming Talk
---

### Post by wildseven on 2007-07-29
Hello, I'm trying to follow the tutorial on the Anjuta website ( [http://www.anjuta.org/documents/C/anjuta-tutorial/x133.html](http://www.anjuta.org/documents/C/anjuta-tutorial/x133.html) ) and I'm getting an error that says 
"undefined reference to GNOME_APP"

Here is the code, I don't understand.
```
#ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gtk/gtk.h>

#include "callbacks.h"
#include "interface.h"
#include "support.h"


void
on_BT_OK_clicked                       ( GtkButton       *button,
                                        gpointer         user_data)
{
	GtkWidget *entry = lookup_widget (GTK_WIDGET(button), "ENTRY"); 
		GtkWidget *msgbox = gnome_app_new("Hello World", "Hello World"); 
		gchar *text1, *text2; 

		text1 = gtk_entry_get_text (GTK_ENTRY(entry)); 
		text2 = g_strconcat ("Hello, ", text1, NULL); 
		gnome_app_message (GNOME_APP(msgbox), text2);
		g_free (text2); 

}


void
on_BT_EXIT_clicked                     (GtkButton       *button,
                                        gpointer         user_data)
{
	gtk_main_quit();
}

```

I don't even want the gui, I just wanted to learn syntax since i'm moving from java to C. But I figure learning to make the gui is convenient as well. Any help would be appreciated. Thank you


-seven.

---

### Post by t3hi3x on 2007-07-29
> **wildseven said:**
> 

...

I don't even want the gui, I just wanted to learn syntax since i'm moving from java to C. But I figure learning to make the gui is convenient as well. Any help would be appreciated. Thank you


-seven.

[http://ubuntuforums.org/showthread.php?t=507345](http://ubuntuforums.org/showthread.php?t=507345)

here is a post on a similar problem i was having. also, i would strongly suggest doing simple command based apps before moving to a gui library.

---

### Post by Geekkit on 2007-07-29
Most likely an includes problem. Make sure you have the following in your makefile:

CFLAGS=-g -Wall `gnome-config --cflags gnome gnomeui`
LDFLAGS=`gnome-config --libs gnome gnomeui`

And then of course use these in your makefile

The GTK+ tutorial shows how to state things at the command prompt:

[http://www.gtk.org/tutorial/x111.html](http://www.gtk.org/tutorial/x111.html)

---

