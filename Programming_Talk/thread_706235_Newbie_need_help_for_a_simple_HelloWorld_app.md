---
title: "Newbie need help for a simple HelloWorld app"
date: 2008-02-24
forum: Programming Talk
---

### Post by johnconnor on 2008-02-24
Hi everyone!

I try to write a simple HelloWorld app using Glade and Python, but when a run my script nothing happens... what's the problem?

Here is my helloworld.py file:

```
#!/usr/bin/env python
# -*- coding: utf8 -*-

import gtk
import gtk.glade

interface = gtk.glade.XML("test.glade")

gtk.main()
```

And here is my test.glade file:

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.0 on Sun Feb 24 14:51:20 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <child>
      <widget class="GtkLabel" id="label1">
        <property name="visible">True</property>
        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
        <property name="label" translatable="yes">HelloWorld</property>
      </widget>
    </child>
  </widget>
</glade-interface>
```

Can anyone help me? Thank you!

---

### Post by twisted_steel on 2008-02-24
Your main window does not have the visible property set to true.  This is what the glade file should look like with it enabled:

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.0 on Sun Feb 24 09:21:30 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <child>
      <widget class="GtkLabel" id="label1">
        <property name="visible">True</property>
        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
        <property name="label" translatable="yes">HelloWorld</property>
      </widget>
    </child>
  </widget>
</glade-interface>
```

The property is set in the glade interface designer by clicking on your main window and then selecting the Common properties tab.  Click the 'visible' button to yes.

---

### Post by johnconnor on 2008-02-24
Thanks a lot I feel so stupid :p :p

---

