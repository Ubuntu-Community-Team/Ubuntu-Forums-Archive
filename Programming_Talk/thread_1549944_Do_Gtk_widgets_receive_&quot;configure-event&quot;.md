---
title: "Do Gtk widgets receive &quot;configure-event&quot; signal?"
date: 2010-08-10
forum: Programming Talk
---

### Post by TheHimself on 2010-08-10
I mean for a widget which is not a Gtk window. In Gdk reference manual it is stated that Gtk discards this event signal for child windows. 
The widget in my program doesn't receive any such signals even though I've enabled all events for it.


I want to be able to do an adjustment to the widget when the Gtk window it belongs to (and therefore the widget) is resized.

---

### Post by TheHimself on 2010-08-12
Any Gtk programmers here?

---

