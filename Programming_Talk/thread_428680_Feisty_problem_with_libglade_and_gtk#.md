---
title: "Feisty: problem with libglade and gtk#"
date: 2007-04-30
forum: Programming Talk
---

### Post by desheikh on 2007-04-30
Hi,
I decided to try out some gui programming.. installed mono, mono-devel, glade-3 and gtk-sharp2


gui.glade:
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.2.0 on Tue May  1 02:39:07 2007 by desheikh@desheikh-->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
        <child>
          <widget class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="label" translatable="yes">label</property>
          </widget>
        </child>
        <child>
          <widget class="GtkButton" id="button1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="label" translatable="yes">button</property>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

glade.cs
```

using System;
using Gtk;
using Glade;
public class GladeApp
{
        public static void Main (string[] args)
        {
                new GladeApp (args);
        }

        public GladeApp (string[] args)
        {
                Application.Init();

                Glade.XML gxml = new Glade.XML (null, "gui.glade", "window1", null);
                gxml.Autoconnect (this);
                Application.Run();
        }
}

```

i compile using 
gmcs -pkg:glade-sharp-2.0 -resource:gui.glade glade.cs

...compiles.... and doesnt run..
Iv been around a lot of places and from what i gather theres some version conflict with the libraries i have installed...
Has anyone else had a similar problem.. any ideas how to resolve?

Ali

---

### Post by desheikh on 2007-04-30
Ok i think there def is some form of version problem... not savvy enough to find out what..
but i create the same layout using glade-2

gui.glade
```

<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkWindow" id="window1">
  <property name="visible">True</property>
  <property name="title" translatable="yes">window1</property>
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

  <child>
    <widget class="GtkVBox" id="vbox1">
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">0</property>

      <child>
	<widget class="GtkLabel" id="label1">
	  <property name="visible">True</property>
	  <property name="label" translatable="yes">label1</property>
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
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkButton" id="button1">
	  <property name="visible">True</property>
	  <property name="can_focus">True</property>
	  <property name="label" translatable="yes">button1</property>
	  <property name="use_underline">True</property>
	  <property name="relief">GTK_RELIEF_NORMAL</property>
	  <property name="focus_on_click">True</property>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>
    </widget>
  </child>
</widget>

</glade-interface>

```

..and viola.. it works!!!

---

