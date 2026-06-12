---
title: "Anyone familiar with custom widgets in gtkmm?"
date: 2009-08-04
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-08-04
I have made my own widget which derives from Gtk::Widget and has it's own Gdk::Window. My problem is that I can't get it to emit the "motion_notify_event" signal. I used the **GDK_POINTER_MOTION_MASK** in the event mask of it's Gdk::Window. I create a new instance of this widget, I connect to the signal_motion_notify_event of this instance but my signal handler never gets called. I am sure I am missing something because if I connect the signal_motion_notify_event in the **widget's constructor** then it's handler gets called. The widget itself doesn't emit this signal in the "outside" world or it gets silenced somewhere else.

Do you have any ideas/suggestions?

---

