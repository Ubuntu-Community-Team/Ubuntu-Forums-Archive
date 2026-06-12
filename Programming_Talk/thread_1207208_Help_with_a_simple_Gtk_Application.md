---
title: "Help with a simple Gtk Application"
date: 2009-07-07
forum: Programming Talk
---

### Post by phmkem on 2009-07-07
Hi I am new to programming Gtk+ and C together and am having a few problems.

The application is supposed to allow the user to put their name in an entry  and then using g_print say hello to them but I get this error:

(tutorial:26000): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(tutorial:26000): Gtk-CRITICAL **: gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed
Hello (null)
I will put the source and the Xml Bellow

Thanks

C Source:
```

#include <gtk/gtk.h>
 
GtkBuilder              *builder;

void
on_hello_clicked(GtkObject *object, gpointer user_data)
{
	const gchar *name;
	GtkWidget *entry1 = GTK_WIDGET(gtk_builder_get_object(builder, "entry1"));
	name = gtk_entry_get_text(GTK_ENTRY(entry1));
	g_print("Hello %s\n", name);
}

void 
on_window1_destroy (GtkObject *object, gpointer user_data)
{
        gtk_main_quit();
	exit(0);
}
 
int
main (int argc, char *argv[])
{
        GtkWidget               *window;
        
        gtk_init (&argc, &argv);
        
        builder = gtk_builder_new ();
        gtk_builder_add_from_file (builder, "tutorial.xml", NULL);
 
        window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
        gtk_builder_connect_signals (builder, NULL);          
        g_object_unref (G_OBJECT (builder));
        
        gtk_widget_show (window);       
        gtk_main ();
        
        return 0;
}

```

The Xml File:

```

<?xml version="1.0"?>
<!--*- mode: xml -*-->
<interface>
  <object class="GtkWindow" id="window">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Hello World of C and Glade</property>
    <property name="type">GTK_WINDOW_TOPLEVEL</property>
    <property name="window_position">GTK_WIN_POS_NONE</property>
    <property name="modal">False</property>
    <property name="resizable">True</property>
    <property name="destroy_with_parent">False</property>
    <property name="decorated">True</property>
    <property name="skip_taskbar_hint">False</property>
    <property name="skip_pager_hint">False</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
    <property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
    <property name="focus_on_map">True</property>
    <property name="urgency_hint">False</property>
    <signal handler="on_window1_destroy" last_modification_time="Wed, 08 Jul 2009 01:42:49 GMT" name="destroy"/>
    <child>
      <object class="GtkFixed" id="fixed1">
        <property name="visible">True</property>
        <child>
          <object class="GtkEntry" id="entry1">
            <property name="width_request">160</property>
            <property name="height_request">27</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="editable">True</property>
            <property name="visibility">True</property>
            <property name="max_length">0</property>
            <property name="text" translatable="yes"/>
            <property name="has_frame">True</property>
            <property name="invisible_char">&#x25CF;</property>
            <property name="activates_default">False</property>
          </object>
          <packing>
            <property name="x">128</property>
            <property name="y">16</property>
          </packing>
        </child>
        <child>
          <object class="GtkButton" id="hello">
            <property name="width_request">104</property>
            <property name="height_request">32</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="relief">GTK_RELIEF_NORMAL</property>
            <property name="focus_on_click">True</property>
            <signal handler="on_hello_clicked" last_modification_time="Wed, 08 Jul 2009 02:33:19 GMT" name="clicked"/>
            <child>
              <object class="GtkAlignment" id="alignment1">
                <property name="visible">True</property>
                <property name="xalign">0.5</property>
                <property name="yalign">0.5</property>
                <property name="xscale">0</property>
                <property name="yscale">0</property>
                <property name="top_padding">0</property>
                <property name="bottom_padding">0</property>
                <property name="left_padding">0</property>
                <property name="right_padding">0</property>
                <child>
                  <object class="GtkHBox" id="hbox1">
                    <property name="visible">True</property>
                    <property name="homogeneous">False</property>
                    <property name="spacing">2</property>
                    <child>
                      <object class="GtkImage" id="image1">
                        <property name="visible">True</property>
                        <property name="stock">gtk-ok</property>
                        <property name="icon_size">4</property>
                        <property name="xalign">0.5</property>
                        <property name="yalign">0.5</property>
                        <property name="xpad">0</property>
                        <property name="ypad">0</property>
                      </object>
                      <packing>
                        <property name="padding">0</property>
                        <property name="expand">False</property>
                        <property name="fill">False</property>
                      </packing>
                    </child>
                    <child>
                      <object class="GtkLabel" id="label1">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Say Hello</property>
                        <property name="use_underline">True</property>
                        <property name="use_markup">False</property>
                        <property name="justify">GTK_JUSTIFY_LEFT</property>
                        <property name="wrap">False</property>
                        <property name="selectable">False</property>
                        <property name="xalign">0.5</property>
                        <property name="yalign">0.5</property>
                        <property name="xpad">0</property>
                        <property name="ypad">0</property>
                        <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
                        <property name="width_chars">-1</property>
                        <property name="single_line_mode">False</property>
                        <property name="angle">0</property>
                      </object>
                      <packing>
                        <property name="padding">0</property>
                        <property name="expand">False</property>
                        <property name="fill">False</property>
                      </packing>
                    </child>
                  </object>
                </child>
              </object>
            </child>
          </object>
          <packing>
            <property name="x">288</property>
            <property name="y">16</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label2">
            <property name="width_request">128</property>
            <property name="height_request">16</property>
            <property name="visible">True</property>
            <property name="label" translatable="yes">Enter your name: </property>
            <property name="use_underline">False</property>
            <property name="use_markup">False</property>
            <property name="justify">GTK_JUSTIFY_LEFT</property>
            <property name="wrap">False</property>
            <property name="selectable">False</property>
            <property name="xalign">0.5</property>
            <property name="yalign">0.5</property>
            <property name="xpad">0</property>
            <property name="ypad">0</property>
            <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
            <property name="width_chars">-1</property>
            <property name="single_line_mode">False</property>
            <property name="angle">0</property>
          </object>
          <packing>
            <property name="x">0</property>
            <property name="y">24</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

---

### Post by monraaf on 2009-07-08
removing the following line should fix it:

```

g_object_unref (G_OBJECT (builder));

```

---

### Post by phmkem on 2009-07-08
Thanks a bunch that fixed it but could you tell me why please so I will understand.

---

### Post by monraaf on 2009-07-08
That line removes the only reference to the builder object, so you can no longer access the builder object after that code is executed. 

You might want to consider using python for GTK+ applications, then you don't have to deal anymore with all this reference counting, casting and other low level nonsense. ;)

---

### Post by phmkem on 2009-07-08
Ok thanks again I'll try that.

---

