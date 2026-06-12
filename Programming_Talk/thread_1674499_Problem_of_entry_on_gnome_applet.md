---
title: "Problem of entry on gnome applet"
date: 2011-01-24
forum: Programming Talk
---

### Post by FireHeron on 2011-01-24
Hi everybody!
Today, I try to write a gnome applet. My applet look like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181832&d=1295847788[/IMG]

My problem is I can not click to type text on entry.
Here is my code:
```

#include <string.h>

#include <gtk/gtk.h>
#include <panel-applet.h>

static gboolean
applet_factory (PanelApplet *applet, const gchar *iid, gpointer user_data)
{
    //GtkWidget *label;
    GtkWidget *toggle;
    GtkWidget *entry;
    GtkWidget *box;

    if (strcmp (iid, "OAFIID:bdict-appletApplet") != 0)
        return FALSE;
    /*
    label = gtk_label_new ("Hello World");
    gtk_container_add (GTK_CONTAINER (applet), label);
    */
    box = gtk_hbox_new (FALSE, 0);
    gtk_container_add (GTK_CONTAINER (applet), box);

    toggle = gtk_toggle_button_new_with_label("A");
    gtk_box_pack_start (GTK_BOX (box), toggle, FALSE, FALSE, 0);
    
    entry = gtk_entry_new ();
    gtk_editable_set_editable (GTK_EDITABLE (entry), TRUE);
    gtk_entry_set_width_chars (GTK_ENTRY (entry), 12);
    gtk_box_pack_end (GTK_BOX (box), entry, FALSE, FALSE, 0);
    
    gtk_widget_show_all (GTK_WIDGET (applet));

    return TRUE;
}

PANEL_APPLET_BONOBO_FACTORY ("OAFIID:bdict-appletApplet_Factory",
                             PANEL_TYPE_APPLET,
                             "GNOME Applet",
                             "0",
                             applet_factory,
                             NULL);


```

Can you help me?
Sorry for my bad English :(.
 [IMG]http://www.flickr.com/photos/58705799@N03/5383736916/[/IMG]

---

