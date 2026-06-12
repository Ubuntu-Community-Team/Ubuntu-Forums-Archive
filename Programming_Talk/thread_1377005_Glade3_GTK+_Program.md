---
title: "Glade3 GTK+ Program"
date: 2010-01-09
forum: Programming Talk
---

### Post by lewisforlife on 2010-01-09
I have a GTK+ program to convert ASCII to the binary representation of the ASCII codes. I am using Glade3 to design the interface.  I am getting some warnings when running my program.  Here is my program:

```

#include <gtk/gtk.h>

gboolean on_window_delete_event (GtkWidget *widget, GdkEvent *event, gpointer user_data)
{

    return FALSE;
}

void on_window_destroy (GtkWidget *widget, gpointer user_data)
{
    g_print ("Hello World\n");
    
    gtk_main_quit ();
}

int main (int argc, char *argv [])
{
    GtkBuilder *builder;
    GtkWidget *window;

    gtk_init (&argc, &argv);

    builder = gtk_builder_new ();
    gtk_builder_add_from_file (builder, "interface.glade", NULL);
    window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));

    gtk_builder_connect_signals (builder, NULL);

    g_object_unref (G_OBJECT (builder));

    gtk_widget_show (window);

    gtk_main ();

    return 0;
}

```

I have attached the glade3 XML code.  I am getting the following warning when running this program:

```

(main:4814): Gtk-WARNING **: Could not find signal handler 'on_window_destroy'

(main:4814): Gtk-WARNING **: Could not find signal handler 'on_window_delete_event'

```

I am compiling the program with:

```

gcc -Wall main.c -o main `pkg-config --cflags --libs gtk+-2.0`

```

I have on_window_destroy and on_window_delete_event functions in my program.  Why am I getting these warnings?

---

### Post by lewisforlife on 2010-01-09
Oops, forgot to post my interface.glade file.  Here is the file attached, and included inline:

```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window">
    <property name="title" translatable="yes">Ascii2Bin</property>
    <property name="default_width">1024</property>
    <property name="default_height">768</property>
    <signal name="destroy" handler="on_window_destroy"/>
    <signal name="delete_event" handler="on_window_delete_event"/>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="orientation">vertical</property>
        <child>
          <object class="GtkMenuBar" id="menubar1">
            <property name="visible">True</property>
            <child>
              <object class="GtkMenuItem" id="menuitem1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem1">
                        <property name="label">gtk-new</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem2">
                        <property name="label">gtk-open</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem3">
                        <property name="label">gtk-save</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem4">
                        <property name="label">gtk-save-as</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkSeparatorMenuItem" id="separatormenuitem1">
                        <property name="visible">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem5">
                        <property name="label">gtk-quit</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem2">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Edit</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu2">
                    <property name="visible">True</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem6">
                        <property name="label">gtk-cut</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem7">
                        <property name="label">gtk-copy</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem8">
                        <property name="label">gtk-paste</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem9">
                        <property name="label">gtk-delete</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem3">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_View</property>
                <property name="use_underline">True</property>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem4">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu3">
                    <property name="visible">True</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem10">
                        <property name="label">gtk-about</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">ASCII</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">automatic</property>
            <property name="vscrollbar_policy">automatic</property>
            <property name="shadow_type">etched-in</property>
            <child>
              <object class="GtkTextView" id="txt_ascii">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label2">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Binary</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="position">3</property>
          </packing>
        </child>
        <child>
          <object class="GtkScrolledWindow" id="scrolledwindow2">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">automatic</property>
            <property name="vscrollbar_policy">automatic</property>
            <property name="shadow_type">etched-in</property>
            <child>
              <object class="GtkTextView" id="txt_bin">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="position">4</property>
          </packing>
        </child>
        <child>
          <object class="GtkButton" id="button1">
            <property name="label" translatable="yes">gtk-convert</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="use_stock">True</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="position">5</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

---

### Post by lewisforlife on 2010-01-10
Here is the solution, when using glade3, compile with:

```
gcc -Wall main.c -o main `pkg-config --cflags --libs gtk+-2.0` -export-dynamic
```

I guess -export-dynamic plays some role in connecting the signals.

---

### Post by geo.cohn on 2011-08-24
-export-dynamic solved my problem as well.  It was driving me nuts, I am using Eclipse and none of the breakpoints that I put in the callbacks were getting hit.  All good now!

---

### Post by JupiterV2 on 2011-08-25
If you intend to port your program to windows you may also need to use G_MODULE_EXPORT in your function prototypes/definitions:

```
G_MODULE_EXPORT void my_callback(void); /* For example */
```

---

