---
title: "Glade3, Gtk and C"
date: 2007-08-09
forum: Programming Talk
---

### Post by netskate on 2007-08-09
Hi all, I have a program like this:
> // GTK regular header
#include <gtk/gtk.h>
// Glade regular header
#include <glade/glade.h>

// Main program
int main(int argc, char **argv) {
    GladeXML    *xml;
    GtkWidget   *widget;

    // Initilize GTK API
    gtk_init(&argc, &argv);
    // Open the Glade file
    xml = glade_xml_new(// Glade file describing the MMI
                        "interfaccia.glade",
                        // Root window (const char)
                        NULL,
                        // Translation domain for XML file
                        NULL);
    // Get the main window container
    widget = glade_xml_get_widget(xml, "window1");
    // We don't handle any signal in this little program
    // but this does not hurt
    glade_xml_signal_autoconnect(xml);
    // Show every widget created so far
    gtk_widget_show_all(widget);
    // Main GTK loop
    gtk_main();

    // Default success code
    return 0;


someone can help me to compile it with gcc?
what is the command line I had to do?

# gcc source.c -o outputfile .....?

wait your answers, thanks

---

### Post by AlexThomson_NZ on 2007-08-09
You probably should be using makefiles at this stage.

Here's a simple makefile I use for my glade/gtk programs that I use as a template (obviously replace 'landscape' with whatever your program is called)

```

CC = gcc
CFLAGS = `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 libnotify`
LIBS = `pkg-config --libs gtk+-2.0 libglade-2.0 libgnomeui-2.0 libnotify`

all: landscape

landscape: landscape.o
	$(CC) landscape.o $(LIBS) -o $@ -export-dynamic
	rm *.o

landscape.o: landscape.c
	$(CC) $(CFLAGS) -o $@ -c $<

clean:
	rm landscape.o landscape

```

Then just ype in 'make' to compile your program!

// Actually you probably don't need the libnotify part- edit that bit out if it doesn't compile because of this

---

