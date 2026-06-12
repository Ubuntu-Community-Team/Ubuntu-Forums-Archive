---
title: "PyGTK TreeView Signal &amp; Events"
date: 2011-08-15
forum: Programming Talk
---

### Post by dcole07 on 2011-08-15
I'm using Pythin 2.7 and pyGTK. I want to override all mouse clicking events with my own function call.

I currently have:
```

...
sw = gtk.ScrolledWindow()
adj = sw.get_vadjustment()
...
self.connect("button_press_event", PyApp.on_key_press)
...
def on_key_press(widget, data=None):
...
    if data.button == 1:
            #print "click ONE"
            if ( adj.get_value() - step >= adj.get_lower() ):
                adj.set_value(adj.get_value() - step )
            else:
                adj.set_value( adj.get_lower() )
...

```

This works fine when I'm NOT in the TreeView Widget, but I want it to work in the TreeView as well. 

My program is a Job List, where I have a TreeView in a ScrolledWindow and a status-bar at the bottom of the window. This means the mouse has to be in the status-bar before my function is ever triggered. 

Back story:
I've setup a computer to display a job list. When the computer is turned on, the Python program starts automatically, and the mouse pointer is in the center of the screen. Users can't move the pointer around because I've modified the mouse to be 3 industrial push buttons that make up interface to this kiosk. Users don't have access to a keyboard or a typical mouse. I modified the mouse because that's the easiest way to add large industrial buttons to a computer.

Thanks.

---

