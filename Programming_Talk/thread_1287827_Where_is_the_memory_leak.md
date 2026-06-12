---
title: "Where is the memory leak?"
date: 2009-10-10
forum: Programming Talk
---

### Post by froggyswamp on 2009-10-10
Folks, valgrind says
> 
==9877== LEAK SUMMARY:
==9877==    definitely lost: 180 bytes in 2 blocks


for this basic hello-world example:
```

#include <gtk/gtk.h>

static void exitApp(GtkWindow *window, gpointer data) {
	gtk_main_quit();
}

int main(int argc, char **argv) {
	gtk_init(&argc, &argv);
	
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(exitApp), NULL);
	gtk_widget_show_all(window);
	
	gtk_main();
	return 0;
}

```

does anyone understand what's the matter? Is there really a memory leak?

---

### Post by napsy on 2009-10-10
valgrind could report a false positive because it can't handle of gtk+ memory management.

You could try to free the window with gtk_widget_destroy() before quitting.

---

### Post by froggyswamp on 2009-10-10
I tried that, and the new code says that although the new window is not null, it's not a widget anymore either, the following code says "window isn't a widget any more":

```

#include <gtk/gtk.h>

static void exitApp(GtkWindow *window, gpointer data) {
	gtk_main_quit();
}

int main(int argc, char **argv) {
	gtk_init(&argc, &argv);
	
	GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(exitApp), NULL);
	gtk_widget_show_all(window);
	
	gtk_main();
	
	if(window != NULL) {
		if(GTK_IS_WIDGET(window)) {
			g_message("destroying window by hand");
			gtk_widget_destroy(window);
			g_message("done.");
		} else {
			g_message("window isn't a widget any more");
		}
	}
	
	return 0;
}

```
The window is probably destroyed in gtk_main_quit(). valgrind probably requires all code to be allocated without g_slice_alloc, GTK probably uses it internally.

---

### Post by dwhitney67 on 2009-10-10
Nice timing!  I was just asking myself the same question this morning.  When is a memory allocation truly a memory leak?

I thought of an analogy... when I turn off the faucet, and one little drop of H20 falls out, and no more, do I have a leak?  Obviously not.

Now, if the faucet, whilst in the "off" position, continues to allow H2O to seep from the spigot, then indeed I have a leak.  It is a continuous, repeating, damn thing, that not only raises my H2O bill, but also keeps me awake at night.

For the one time allocation, that never "bothers" anyone or anything, and that is never de-allocated, is that a leak?  Heck no!  When the application is terminated, the system will cheerfully retake that chunk of memory, thus allowing it to be used by another application.

Hopefully my deep-thoughts will help to enlighten the masses.

Now back to my fishing....

---

### Post by MadCow108 on 2009-10-10
add the gtk_widget_destroy to your destroy callback, gtk_main quit messes with the pointer (maybe even destroys it)

here are some information on memory leaks with valgrind and gtk:
[http://live.gnome.org/Valgrind](http://live.gnome.org/Valgrind)
you can turn of the g_slice alloc but you'll still have memory leaks in gtk_init
but as dwhitney explained with this nice analogy, this is a one time leak which won't harm (except you have incredible little memory available, but then you shouldn't be using gtk in the first place)

---

### Post by froggyswamp on 2009-10-10
I added the call to gtk_widget_destroy(window) inside exitApp() but same result.
I googled but couldn't find about memory leaks in gtk_init(), would you please paste a link to read about this?

---

### Post by MadCow108 on 2009-10-10
the only thing I found was this:
[http://www.mail-archive.com/gtk-list@redhat.com/msg00414.html](http://www.mail-archive.com/gtk-list@redhat.com/msg00414.html)

I ran your program through valgrind with the settings recommended by gtk and the only leaks where in gtk_init
(--leak-check=full gives you line numbers if you have debugging symbols)

this function gets executed only once in a program so you can ignore the memory lost

---

