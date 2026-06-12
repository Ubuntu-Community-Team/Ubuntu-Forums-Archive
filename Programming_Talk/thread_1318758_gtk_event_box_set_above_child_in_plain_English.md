---
title: "gtk_event_box_set_above_child in plain English?"
date: 2009-11-07
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-07
Folks I read the docs on this function 100 times but I still don't get what problem it solves.
Can anyone explain in plain English please?

> 
Set whether the event box window is positioned above the windows of its child, as opposed to below it. If the window is above, all events inside the event box will go to the event box. If the window is below, events in windows of child widgets will first got to that widget, and then to its parents.

I also suspect that "got" is a typo, should be "go".
Also "all events inside the event box will go to the event box" is imho wonderful, I don't get it how one "being inside house A" can "go to house A".

---

### Post by SledgeHammer_999 on 2009-11-07
This is a special case(I suppose) when you put a widget inside an eventbox and that widget ALREADY can receive events. Events related to X (like motion/clicking/focus) are received by the corresponding gdk_window. If eventbox's gdk_window(invisible obviously) is above the widget's gdk_window then eventbox will receive the event INSTEAD of the widget.

I repeat, this has a meaning if the widget already has a gdk_window associated with it.

If you are still confused try asking something more specific.

ps. yes "got" is a typo as it seams

---

### Post by froggyswamp on 2009-11-07
Thanks, in other words if eventbox's window is "above" widget's gdk_window then neither the widget nor its children (if any) will receive the event?

---

### Post by SledgeHammer_999 on 2009-11-07
correct.

---

### Post by froggyswamp on 2009-11-08
thanks a lot!

---

