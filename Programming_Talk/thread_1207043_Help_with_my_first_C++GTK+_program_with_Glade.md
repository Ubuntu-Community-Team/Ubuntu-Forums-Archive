---
title: "Help with my first C++/GTK+ program with Glade"
date: 2009-07-07
forum: Programming Talk
---

### Post by Morais on 2009-07-07
Hello,

I am curently doing an application with GUI that needs to sort elements of a given array size. The sort part is already implemented and all I need to is the graphical interface, which im stuck at this moment.
I am using Glade 3.6.7, GTK 2.16 and gcc 4.4 on x86-64.
This is a screenshot of the gui:
[IMG]http://www.abload.de/img/screenshot-a.outroxu.png[/IMG]

The entry text is the array size, the buttons below are the sorting algorithms.The left text field will display the original array and the right text field will  display the array sorted.

How can I get the value from the text entry when I click any of the buttons for calling my sorting functions? Can I do it inside the on_button<x>_clicked functions? Already tried with gtk_entry_get_text, but done wrong.

Here are the source-codes

.glade file (with signifcant parts bold):
```
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="window_position">center-always</property>
    <signal name="destroy" handler="gtk_main_quit"/>
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
          <object class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <object class="GtkScrolledWindow" id="scrolledwindow1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="hscrollbar_policy">automatic</property>
                <property name="vscrollbar_policy">automatic</property>
                <child>
                  <object class="GtkTextView" id="textview1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>
                  </object>
                </child>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkVBox" id="vbox2">
                <property name="visible">True</property>
                <property name="orientation">vertical</property>
                <child>
                 [B] <object class="GtkEntry" id="entry1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="has_focus">True</property>
                    <property name="max_length">10</property>
                    <property name="invisible_char">&#x2022;</property>
                    <property name="xalign">0.5</property>
                  </object>[/B]
                  <packing>
                    <property name="expand">False</property>
                    <property name="position">0</property>
                  </packing>
                </child>
                <child>
                  [B]<object class="GtkButton" id="button1">
                    <property name="label" translatable="yes">Bolha</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <signal name="clicked" handler="on_button1_clicked"/>
                  </object>[/B]
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="button2">
                    <property name="label" translatable="yes">Sele&#xE7;&#xE3;o</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                  </object>
                  <packing>
                    <property name="position">2</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="button3">
                    <property name="label" translatable="yes">Inser&#xE7;&#xE3;o</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                  </object>
                  <packing>
                    <property name="position">3</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="button4">
                    <property name="label" translatable="yes">Merge</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                  </object>
                  <packing>
                    <property name="position">4</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="button5">
                    <property name="label" translatable="yes">Quick</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                  </object>
                  <packing>
                    <property name="position">5</property>
                  </packing>
                </child>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <object class="GtkScrolledWindow" id="scrolledwindow2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="hscrollbar_policy">automatic</property>
                <property name="vscrollbar_policy">automatic</property>
                <child>
                  <object class="GtkTextView" id="textview2">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>
                  </object>
                </child>
              </object>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>
```

Here is the cpp.
```
#include <gtk/gtk.h>
extern "C" void on_button1_clicked (/*GtkObject *object, gpointer user_data*/)
{
		/* Get the entry1 value and call the generating array function, passing the value as a parameter and sort this array.*/
}
extern "C" void on_button2_clicked (/*GtkObject *object, gpointer user_data*/)
{
		/* Get the entry1 value and call the generating array function, passing the value as a parameter and sort this array.*/
}
extern "C" void on_button3_clicked (/*GtkObject *object, gpointer user_data*/)
{
		/* Get the entry1 value and call the generating array function, passing the value as a parameter and sort this array.*/
}
extern "C" void on_button4_clicked (/*GtkObject *object, gpointer user_data*/)
{
		/* Get the entry1 value and call the generating array function, passing the value as a parameter and sort this array.*/
}
extern "C" void on_button5_clicked (/*GtkObject *object, gpointer user_data*/)
{
		/* Get the entry1 value and call the generating array function, passing the value as a parameter and sort this array.*/
}
/*

ALL OTHER FUNCTIONS

*/

int
main (int argc, char *argv[])
{
        GtkBuilder              *builder;
        GtkWidget               *window1;
        
        gtk_init (&argc, &argv);
        
        builder = gtk_builder_new ();
        gtk_builder_add_from_file (builder, "teste2.glade", NULL);
 
        window1 = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
        gtk_builder_connect_signals (builder, NULL);          
        g_object_unref (G_OBJECT (builder));
        
        gtk_widget_show (window1);       
        gtk_main ();
        
        return 0;
}

```

Any input is welcome ):P!

---

### Post by SledgeHammer_999 on 2009-07-07
I can't answer your question. But I have a question for you:
Since you're using C++, have you considered using [Gtkmm and libglademm](www.gtkmm.org) (glademm [documentation](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html))?
(they are C++ bindings for gtk and glade)

---

### Post by days_of_ruin on 2009-07-07
The easiest way I can think of to do this would be to make the entry a global variable (just like window1 is). Also you should rename the widgets so they have more descriptive names. Like the other poster said you might want to use gtkmm instead.

---

### Post by Morais on 2009-07-08
> **SledgeHammer_999 said:**
> I can't answer your question. But I have a question for you:
Since you're using C++, have you considered using [Gtkmm and libglademm](www.gtkmm.org) (glademm [documentation](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html))?
(they are C++ bindings for gtk and glade)
Thanks for the quick answer and the links. This is a homework from my university and my teacher said object-oriented is mandatorily. Thanks Ill consider it.

> **days_of_ruin said:**
> The easiest way I can think of to do this would be to make the entry a global variable (just like window1 is). Also you should rename the widgets so they have more descriptive names. Like the other poster said you might want to use gtkmm instead.

Thanks, Ill give it a go!

---

