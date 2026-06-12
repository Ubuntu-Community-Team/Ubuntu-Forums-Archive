---
title: "[pygtk] key press handling... HELP!!!"
date: 2009-02-10
forum: Programming Talk
---

### Post by days_of_ruin on 2009-02-10
```
self.window.connect("key-press-event",self.on_window_key_press_event)
```
Okay so I have the window handle key press events

```
def on_window_key_press_event(self,window,event):
        print event.state
        if event.state == gtk.gdk.MOD2_MASK:
            print "Control"
        if event.keyval == 122:
            print "z":w

```

But no matter what key I press the console always prints
```
<flags GDK_MOD2_MASK of type GdkModifierType>
Control
```

Why does it do that??

---

### Post by days_of_ruin on 2009-02-10
Okay I still have no idea what MOD2_MASK means but I figured out how to
tell if the user pressed control + z
```
if event.keyval == 122:
            if event.state == gtk.gdk.CONTROL_MASK | gtk.gdk.MOD2_MASK:
                print "Control + z"

```

Is there a gtk.gdk key constants for a-z? To make the code more readable.

---

### Post by MeanEYE on 2009-11-03
> **days_of_ruin said:**
> Okay I still have no idea what MOD2_MASK means but I figured out how to
tell if the user pressed control + z
```
if event.keyval == 122:
            if event.state == gtk.gdk.CONTROL_MASK | gtk.gdk.MOD2_MASK:
                print "Control + z"

```

Is there a gtk.gdk key constants for a-z? To make the code more readable.

Sorry for late reply :)  The reason you got both of lines printed is because Control is a key too, so event was first fired when user pressed Control key and later for Z too. :) Under event.state you have bit mask representing state of modifiers (ALT, SHIFT, SUPER, CONTROL... etc.).

```

import gtk.gdk

def click_event(self, widget, event):
    print gtk.gdk.keyval_name(event.keyval)

```

This will give you output like "Control_L", "Tab", "z", "s"

Hope this helps!

---

### Post by migule on 2011-02-15
In my system, GDK_MOD2_MASK is mapped to the numerical lock. 

You can run xmodmap to see the keymap table of your system.

---

