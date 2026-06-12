---
title: "C, Glade, GTK"
date: 2009-05-18
forum: Programming Talk
---

### Post by matmatmat on 2009-05-18
I've created a program with glade:
```

<?xml version="1.0"?>
<interface>
  <!-- interface-requires gtk+ 2.16 -->
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <signal handler="destroy_event" name="destroy_event"/>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="orientation">vertical</property>
        <child>
          <object class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <object class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Number of charecters</property>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkSpinButton" id="number">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
                <property name="climb_rate">1</property>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <child>
              <object class="GtkLabel" id="label2">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Password</property>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="entry">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkHBox" id="hbox3">
            <property name="visible">True</property>
            <child>
              <object class="GtkButton" id="button1">
                <property name="label" translatable="yes">Generate</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal handler="generate" name="clicked"/>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button2">
                <property name="label" translatable="yes">Quit</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal handler="destroy_event" name="clicked"/>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```
glade ^
```

#include <gtk/gtk.h>
 
void destroy_event (GtkObject *object, gpointer user_data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
    GtkBuilder      *builder; 
    GtkWidget       *window;
 
    gtk_init (&argc, &argv);
 
    builder = gtk_builder_new ();
    gtk_builder_add_from_file (builder, "guipasswrdgenerator.xml", NULL);
    window = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
    gtk_builder_connect_signals (builder, NULL);
 
    g_object_unref (G_OBJECT (builder));
        
    gtk_widget_show (window);                
    gtk_main ();
 
    return 0;
}

```
when run I run it the spin button isn't editable

---

### Post by days_of_ruin on 2009-05-18
It needs to have an adjustment.

---

### Post by matmatmat on 2009-05-19
Wat do you mean by adjustment 
```

<property name="adjustment">1</property>

```
I cant see any "adjustment" in glade

---

### Post by days_of_ruin on 2009-05-19
See screenshot. ;)

---

