---
title: "Glade: Show a window, should be trivial..."
date: 2008-11-02
forum: Programming Talk
---

### Post by tom66 on 2008-11-02
OK, silly question, but how do I show a window by name in a glade C++ application? Here is my code...

```

#include <gtk/gtk.h>
#include <glade/glade.h>

int main(int argc, char *argv[])
{
	GladeXML *xml;
	
	gtk_init(&argc, &argv);
	xml = glade_xml_new("lsspc.glade", NULL, NULL);
	
	glade_xml_signal_autoconnect(xml);
	
	/* show the startup dialog */
	GtkWidget* startup_dialog = lookup_widget(GTK_WIDGET(window), "welcome-dialog"); /* this doesn't work. */
	
	/* start the event loop */
	gtk_main();
	
	return 0;
}

```

---

### Post by kknd on 2008-11-02
gtk_widget_show_all(startup_dialog);

---

### Post by slavik on 2008-11-03
that or set the visible = true for the main window (glade sets it to false by default).

---

### Post by tom66 on 2008-11-03
That should work, but am I fetching the widget correctly? I get a few errors, when compiling: 

lsspc.c: In function ‘main’:
lsspc.c:14: error: ‘window’ undeclared (first use in this function)
lsspc.c:14: error: (Each undeclared identifier is reported only once
lsspc.c:14: error: for each function it appears in.)
lsspc.c:14: warning: initialization makes pointer from integer without a cast

Help appreciated!

---

### Post by kknd on 2008-11-03
The correct is:

GtkWidget my_window = glade_xml_get_widget(xml, "mywidgetname");

---

### Post by kknd on 2008-11-03
Double post.

---

