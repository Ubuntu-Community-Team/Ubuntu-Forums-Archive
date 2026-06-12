---
title: "GTK+ help"
date: 2006-12-24
forum: Programming Talk
---

### Post by Hairy_Palms on 2006-12-24
hi, im having problems with gtk, it tells me lookup_widget is not valid even though it should be,

```
// generated 2006/12/24 23:52:56 GMT by mike@mikesdesktop.(none)
// using glademm V2.6.0
//
// newer (non customized) versions of this file go to window1.cc_new

// This file is for your program, I won't touch it again!

#include "config.h"
#include "window1.hh"
#include <gtk/gtk.h>

void window1::on_button2_clicked()
{  
gtk_main_quit();
}


void on_button1_clicked(GtkButton *button, gpointer user_data)
{

GtkWidget * label = lookup_widget(GTK_WIDGET(button), "label1");
GtkWidget * entry = lookup_widget(GTK_WIDGET(button), "entry1");

gchar output[50]="Hello ";
strcat(output,gtk_entry_get_text(GTK_ENTRY(entry)));
gtk_label_set_text(GTK_LABEL(label),output);

} 


```

the problem is with the lines here
> GtkWidget * label = lookup_widget(GTK_WIDGET(button), "label1");
GtkWidget * entry = lookup_widget(GTK_WIDGET(button), "entry1");
any ideas? thx in advance

---

### Post by Hairy_Palms on 2006-12-26
shameless bump

---

### Post by lnostdal on 2006-12-26
i can't seem to find `lookup_widget' in the API-docs of neither Glade nor GTK+

but regardless of this you should have Glade generating XML instead of code, then use libglade to load and generate the GUI at runtime from the XML-files ... you'll see this mentioned many places; [http://www.gtk.org/faq/#AEN395](http://www.gtk.org/faq/#AEN395) ...

---

### Post by Hairy_Palms on 2006-12-26
hmmm if lookup_widget isnt right do you know how i get input from an textinputbox?
i thought lookup widget was right from here
[http://www.gtk.org/faq/#AEN395](http://www.gtk.org/faq/#AEN395)

---

### Post by lnostdal on 2006-12-26
> **Hairy_Palms said:**
> hmmm if lookup_widget isnt right do you know how i get input from an textinputbox?
i thought lookup widget was right from here
[http://www.gtk.org/faq/#AEN395](http://www.gtk.org/faq/#AEN395)


I assume you mean the widget `GtkEntry' when you say "textinputbox".

See: [http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html) which leads you too [http://developer.gnome.org/doc/API/2.0/gtk/GtkEntry.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkEntry.html) which in turn leads you too [http://developer.gnome.org/doc/API/2.0/gtk/GtkEntry.html#gtk-entry-get-text](http://developer.gnome.org/doc/API/2.0/gtk/GtkEntry.html#gtk-entry-get-text)

also see: [http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html](http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html) ...

---

### Post by Hairy_Palms on 2006-12-27
hmm i was messin about with it before i saw your latest post, it works now but i didnt change anything except the button type, i changed the button to gtk-ok instead of leaving it blank..
my code now looks like
> #ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gtk/gtk.h>

#include "callbacks.h"
#include "interface.h"
#include "support.h"


void
on_button1_clicked                     (GtkButton       *button,
                                        gpointer         user_data)
{
GtkWidget * label = lookup_widget(GTK_WIDGET(button), "label1");
GtkWidget * entry = lookup_widget(GTK_WIDGET(button), "entry1");

gchar output[50]="Hello ";
strcat(output,gtk_entry_get_text(GTK_ENTRY(entry)));
gtk_label_set_text(GTK_LABEL(label),output);

}




void
on_button2_clicked                     (GtkButton       *button,
                                        gpointer         user_data)
{
 gtk_main_quit();

}



i assume it needed the interface.h

---

