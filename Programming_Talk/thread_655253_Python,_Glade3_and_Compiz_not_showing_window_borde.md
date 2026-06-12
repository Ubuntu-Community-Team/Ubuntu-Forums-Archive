---
title: "Python, Glade3 and Compiz not showing window border"
date: 2008-01-01
forum: Programming Talk
---

### Post by jordilin on 2008-01-01
I just made a little app with a label and button in glade3 and used a little python program to execute it. The problem is that no window border appears. Compiz is running, but all other windows run fine with their borders. If I deactivate desktop effects, then the application appears with its corresponding window border. Really weird. 
Anybody can figure out why my simple app does not draw the window border when Compiz is running?

---

### Post by samjh on 2008-01-01
Do you mind perhaps making the Python script and Glade file available?  I just tried a simple PyGTK + Glade application under Compiz-Fusion, and it runs fine.

---

### Post by jordilin on 2008-01-01
> **samjh said:**
> Do you mind perhaps making the Python script and Glade file available?  I just tried a simple PyGTK + Glade application under Compiz-Fusion, and it runs fine.

I just attach them, but they are very, very simple. 
glade file:
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.0 on Tue Jan  1 15:53:50 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="holamonMainWindow">
    <property name="visible">True</property>
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <property name="border_width">1</property>
    <property name="title" translatable="yes">Hola Mon</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_MENU</property>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
        <child>
          <widget class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="label" translatable="yes">Click Below!!!!</property>
          </widget>
        </child>
        <child>
          <widget class="GtkButton" id="btnHolaMon">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="label" translatable="yes">Just click!!!
</property>
            <property name="response_id">0</property>
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

and the python program that loads this file:
```

#!/usr/bin/python
import sys

try:
        import pygtk
        pygtk.require("2.0")
except:
        pass
try:
        import gtk
        import gtk.glade
except:
        sys.exit(1)


class HolaMonGTK:
        """holamon GTK app"""
        def __init__(self):
                self.gladefile="HolaMon.glade"
                self.wTree=gtk.glade.XML(self.gladefile)
                self.window=self.wTree.get_widget("holamonMainWindow")
                if (self.window):
                        self.window.connect("destroy",gtk.main_quit)

if __name__=="__main__":
        hol= HolaMonGTK()
        gtk.main()

```

Perhaps, I am missing enabling some property. I don't know :confused:

---

### Post by jordilin on 2008-01-01
I just installed glade2, and it runs fine :) designing the app with glade2. Weird.

---

### Post by samjh on 2008-01-02
Found the problem.

The "Type hint" for your holamonMainWindow needs to be either Normal or Dialog.

I don't know why that is a problem with Compiz, but anyway, I've given you a solution. :)

---

### Post by jordilin on 2008-01-02
> **samjh said:**
> Found the problem.

The "Type hint" for your holamonMainWindow needs to be either Normal or Dialog.

I don't know why that is a problem with Compiz, but anyway, I've given you a solution. :)

Thanks, it must be either Normal or Dialog.

---

