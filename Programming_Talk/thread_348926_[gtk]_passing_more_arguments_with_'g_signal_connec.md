---
title: "[gtk] passing more arguments with 'g_signal_connect'"
date: 2007-01-29
forum: Programming Talk
---

### Post by lazka on 2007-01-29
Hi,

started learning gk+ today.... problems everywhere ;)

I have a simple window with 3 text-entries and a button.
i want to pass the content of all three text-fields to the function.

```

static void callback( GtkWidget *widget, gpointer in, gpointer out, gpointer key )
{
    g_print ("%s - %s - %s\n", (char *) in, (char *) out, (char *) key);
}

int main(int argc, char **argv)
{
......
	entry_input = glade_xml_get_widget(xml, "entry1");
	entry_output = glade_xml_get_widget(xml, "entry2");
	entry_xor = glade_xml_get_widget(xml, "entry3");


	button_ok = glade_xml_get_widget(xml, "button2");
	g_signal_connect (G_OBJECT (button_ok), "clicked", G_CALLBACK (callback), (gpointer) gtk_entry_get_text(GTK_ENTRY(entry_input)), (gpointer) gtk_entry_get_text(GTK_ENTRY(entry_output)), (gpointer) gtk_entry_get_text(GTK_ENTRY(entry_xor)) );
.....
}

```

but... : "macro "g_signal_connect" passed 6 arguments, but takes just 4"

how can i do this without global vars?

---

### Post by lnostdal on 2007-01-29
simple; put your widgets in a structure or array :)

use the same solution whenever you meet a situation like this .. also, C has only support for returning _one_ value from a function; quite a limitation for one with a vivid imagination :)

---

### Post by lazka on 2007-01-29
ahhh crap, now i know why i hated C.. :wink:

---

