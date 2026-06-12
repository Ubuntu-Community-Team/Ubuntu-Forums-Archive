---
title: "GLADE and PyGTK GtkTextView unable to edit/type"
date: 2013-07-14
forum: Programming Talk
---

### Post by slooksterpsv on 2013-07-14
I've created a window following a tutorial via Glade and PyGTK; but when I click in the box to edit it, no cursor shows up and when typing nothing shows up either. Yet I can paste text into it, here's the Glade file as well as the python file:

```

<?xml version="1.0" encoding="UTF-8"?>
<interface>
  <!-- interface-requires gtk+ 3.0 -->
  <object class="GtkTextBuffer" id="textbuffer1"/>
  <object class="GtkWindow" id="window1">
    <property name="can_focus">False</property>
    <property name="default_width">250</property>
    <property name="default_height">300</property>
    <signal name="delete-event" handler="onDeleteWindow" swapped="no"/>
    <child>
      <object class="GtkBox" id="box1">
        <property name="visible">True</property>
        <property name="can_focus">False</property>
        <property name="orientation">vertical</property>
        <child>
          <object class="GtkMenuBar" id="menubar1">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <child>
              <object class="GtkMenuItem" id="menuitem1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem1">
                        <property name="label">gtk-new</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem2">
                        <property name="label">gtk-open</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem3">
                        <property name="label">gtk-save</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem4">
                        <property name="label">gtk-save-as</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkSeparatorMenuItem" id="separatormenuitem1">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem5">
                        <property name="label">gtk-quit</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <signal name="activate" handler="onDeleteWindow" swapped="no"/>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem2">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="label" translatable="yes">_Edit</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu2">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem6">
                        <property name="label">gtk-cut</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem7">
                        <property name="label">gtk-copy</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem8">
                        <property name="label">gtk-paste</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem9">
                        <property name="label">gtk-delete</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
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
                <property name="can_focus">False</property>
                <property name="label" translatable="yes">_View</property>
                <property name="use_underline">True</property>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem4">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu3">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="imagemenuitem10">
                        <property name="label">gtk-about</property>
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
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
            <property name="fill">True</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="shadow_type">in</property>
            <child>
              <object class="GtkTextView" id="textview1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="events">GDK_EXPOSURE_MASK | GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_MOTION_MASK | GDK_BUTTON1_MOTION_MASK | GDK_BUTTON2_MOTION_MASK | GDK_BUTTON3_MOTION_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK | GDK_KEY_PRESS_MASK | GDK_KEY_RELEASE_MASK | GDK_ENTER_NOTIFY_MASK | GDK_LEAVE_NOTIFY_MASK | GDK_FOCUS_CHANGE_MASK | GDK_STRUCTURE_MASK | GDK_PROPERTY_CHANGE_MASK | GDK_VISIBILITY_NOTIFY_MASK | GDK_PROXIMITY_IN_MASK | GDK_PROXIMITY_OUT_MASK | GDK_SUBSTRUCTURE_MASK | GDK_SCROLL_MASK | GDK_TOUCH_MASK | GDK_SMOOTH_SCROLL_MASK</property>
                <property name="wrap_mode">char</property>
                <property name="buffer">textbuffer1</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkStatusbar" id="statusbar1">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="orientation">vertical</property>
            <property name="spacing">2</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">2</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>


```

```

from gi.repository import Gtk

class Handler:
    def onDeleteWindow(self, *args):
        Gtk.main_quit(*args)

    def onButtonPressed(self, button):
        print "Hello World!"
	Gtk.main_quit()

builder = Gtk.Builder()
builder.add_from_file("test1.glade")
builder.connect_signals(Handler())

window = builder.get_object("window1")
window.show_all()

Gtk.main()


```

---

### Post by slooksterpsv on 2013-07-14
GTK 2 works, its just gtk3, is there not a pygtk binding for gtk3?

---

### Post by eightbits2010 on 2013-07-30
Well, I too am struggling to use Glade. I am using python 2.7.3, Glade 3.8.0 on Ubuntu 12.04.
I have spent hours/days reading, searching the internet, read quite a few tutorials and still do not have a firm grasp
on writting even a simple example.

Most of the tutorials seem to be old, the code is not formated and in several cases uses C/C++ an the language.
Is there anyone who can point me to a simple example to follow?

 I was using one that was named "adder" which seemed pretty good , but it was impossible to watch the youtube version and the online version looked pretty good but did not work as I thought that it should.

I don't think I am having a hugh problem is setting the GUI part using glade, but generating the python code is still causing
me the most problems. Some of the examples seem to require code statements but are not coded that way in other examples.:( Most of these issues seem to be about the setting up of required statements about GTK methods/attributes.

Is there a suggest site tutorial and or a book I need to read?

Thanks if I can get any suggestions/help.

---

