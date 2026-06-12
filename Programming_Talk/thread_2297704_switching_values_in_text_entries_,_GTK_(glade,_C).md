---
title: "switching values in text entries , GTK (glade, C)"
date: 2015-10-06
forum: Programming Talk
---

### Post by Mr.Kumar on 2015-10-06
I was trying to switch values from one  text entry to another but I am getting a segfault I have looked and didn't seem to find how to resolve it.  I am new to gtk/glade so this might be very silly error which I am not able figure out. Any help is appreciated.

Code:

includes/asitor.h:
```

include <stdio.h>
#include <gtk/gtk.h>
#include <stdlib.h>
#include <string.h>

```

main.c: 
```

#include "includes/asitor.h"
 
typedef struct loginer {
    GtkEntry *entry_uname; //username textbox
    GtkEntry *entry_upass; //pasword textbox
}txtboxes;

G_MODULE_EXPORT void on_login_destroy ()
{
    gtk_main_quit ();
}

G_MODULE_EXPORT void on_login_btn_clicked(GtkButton *button, txtboxes* gtexters){
    char luemail[255];
    char lupass[255];

    //getting text from the text boxes
     const gchar *emailer = gtk_entry_get_text(gtexters->entry_uname);
     const gchar *passer = gtk_entry_get_text(gtexters->entry_upass);

     // getting text from text boxes (input)
     strcpy(luemail, emailer);
     strcpy(lupass, passer);


     //reversing and setting new text (output)
     gtk_entry_set_text(gtexters->entry_uname, lupass);
     gtk_entry_set_text(gtexters->entry_upass, luemail);
}

int main(int argc, char **argv){
    GtkBuilder *builder;
    GtkWidget *window;
    txtboxes gtexters;
    GError *error = NULL;
    /* Init GTK+ */
    gtk_init( &argc, &argv );

    /* Create new GtkBuilder object */
    builder = gtk_builder_new();
    /* Load UI from file. If error occurs, report it and quit application.
     Replace "gui/login.glade" with your saved project with your startup form.*/
    if( ! gtk_builder_add_from_file( builder, "gui/login.glade", &error )){
        g_warning( "%s", error->message );
        g_free( error );
        return( 1 );
    }
    /* Get main window pointer from UI */
    window = GTK_WIDGET( gtk_builder_get_object( builder, "login" ) );
    
    //connecting each structure member to it appropriate gtkwidget
    
    gtexters.entry_uname = GTK_ENTRY(gtk_builder_get_object(builder, "entry_uname" ));
    gtexters.entry_upass = GTK_ENTRY(gtk_builder_get_object(builder, "entry_upass" )); 

    /* Connect signals with appropriate handlers so that handlers could be called when button is clicked */
    gtk_builder_connect_signals( builder, &gtexters);
    /* Destroy builder, since we don't need it anymore */
    g_object_unref( G_OBJECT( builder ) );
    /* Show window. All other widgets are automatically shown by GtkBuilder */
    gtk_widget_show( window );
    /* Start main loop */
    gtk_main();
    return 0;
}

```

glade file:

```

<?xml version="1.0" encoding="UTF-8"?>
<interface>
  <requires lib="gtk+" version="2.24"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="login">
    <property name="can_focus">False</property>
    <property name="border_width">46</property>
    <property name="title" translatable="yes">Asitor Login</property>
    <property name="default_width">440</property>
    <property name="default_height">250</property>
    <signal name="destroy" handler="gtk_main_quit" swapped="no"/>
    <child>
      <object class="GtkVBox" id="vbox2">
        <property name="visible">True</property>
        <property name="can_focus">False</property>
        <property name="spacing">15</property>
        <child>
          <object class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <child>
              <object class="GtkLabel" id="uname">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="label" translatable="yes">User Email:</property>
                <property name="ellipsize">start</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="entry_umail">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="tooltip_text" translatable="yes">Enter your username here</property>
                <property name="invisible_char">&#9679;</property>
                <property name="primary_icon_activatable">False</property>
                <property name="secondary_icon_activatable">False</property>
                <property name="primary_icon_sensitive">True</property>
                <property name="secondary_icon_sensitive">True</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <child>
              <object class="GtkLabel" id="upass">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="xalign">0.47999998927116394</property>
                <property name="label" translatable="yes">Password:</property>
                <property name="ellipsize">start</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="entry_upass">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="tooltip_text" translatable="yes">Enter your password here</property>
                <property name="invisible_char">&#9679;</property>
                <property name="primary_icon_activatable">False</property>
                <property name="secondary_icon_activatable">False</property>
                <property name="primary_icon_sensitive">True</property>
                <property name="secondary_icon_sensitive">True</property>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkHBox" id="hbox3">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="spacing">73</property>
            <child>
              <object class="GtkButton" id="login_btn">
                <property name="label" translatable="yes">Login</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="tooltip_text" translatable="yes">Press to login to Asitor</property>
                <property name="use_action_appearance">False</property>
                <signal name="clicked" handler="on_login_btn_clicked" swapped="no"/>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="padding">4</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="cancle_btn">
                <property name="label" translatable="yes">Exit</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="tooltip_text" translatable="yes">Press to exit from Asitor</property>
                <property name="use_action_appearance">False</property>
                <signal name="clicked" handler="gtk_main_quit" swapped="no"/>
              </object>
              <packing>
                <property name="expand">True</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="padding">15</property>
            <property name="position">2</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>


```

this is the error I am getting:

```

(asitor:30027): Gtk-CRITICAL **: IA__gtk_entry_get_text: assertion 'GTK_IS_ENTRY (entry)' failed
Segmentation fault


```

---

### Post by spjackson on 2015-10-06
> 
```

    <object class="GtkEntry" id="entry_umail">

    gtexters.entry_uname = GTK_ENTRY(gtk_builder_get_object(builder, "entry_uname" ));

```

These names don't match so gtexters.entry_uname is NULL. Change either your source or the glade file so that they match.

---

### Post by Mr.Kumar on 2015-10-06
yes, thank you. :KS

---

