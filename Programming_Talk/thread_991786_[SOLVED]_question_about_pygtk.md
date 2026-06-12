---
title: "[SOLVED] question about pygtk"
date: 2008-11-24
forum: Programming Talk
---

### Post by giuspen on 2008-11-24
I don't understand why, defining a method like this in pygtk:
[PHP]def delete_event(self, widget, event, data=None):
   pass[/PHP]
I have to include the arguments "widget" and "event" even if I will not use them, otherwise it will not work.
In the tutorial this is not explained and for me is quite important. Thanks to anybody can clarify this to me.

---

### Post by crazyfuturamanoob on 2008-11-24
> **giuspen said:**
> I don't understand why, defining a method like this in pygtk:
[PHP]def delete_event(self, widget, event, data=None):
   pass[/PHP]
I have to include the arguments "widget" and "event" even if I will not use them, otherwise it will not work.
In the tutorial this is not explained and for me is quite important. Thanks to anybody can clarify this to me.

In GTK, programmers must define their own widget delete events (and some others too) and tell the widget, 
what function is executed when widget is deleted.

The GTK widget passes those two arguments to the self-defined delete function, in case the user needs them.
The arguments are needed in the function because if you pass arguments to a function which doesn't take any, it doesn't work.

Probably in the example you got, there is no need for the arguments, and the delete event is also empty, to make the example easier to understand.

Somebody *über-pr0 master hacker programmer geek* needs to confirm this, I'm not 100% sure about this.

---

### Post by Tony Flury on 2008-11-24
in python you have two main types of arguments, mandatory and optional. Take this function definition : 

```

def function(title, event, widget, data=None)

```

In this function the arguments title, event and widget are mandatory and have to be passed to the function. The data argument is optional, and does not have to be passed. If it is not provided it takes the value of None.

---

