---
title: "Gtkmm/libglademm updating a GUI"
date: 2009-05-14
forum: Programming Talk
---

### Post by C-- on 2009-05-14
I have a GTK+ window built in Glade and parsed with libglademm and gtkmm (the C++ GTK+ wrapper). I have a separated POSIX thread that is trying to update a Gtk::Label every second with the current system time, but once the window is visible it will not update. Plus, one of the icons I specified in glade is a flashing .gif, and while the .gif animates in the Glade preview version of the window, it does not flash at all when the executable runs. It appears that in both cases the GUI will not update.

---

### Post by haTem on 2009-05-14
Have a look at Glib::Dispatcher. It has been awhile since I've used gtkmm, but I do recall that Glib::Dispatcher allows for cross-thread signaling, which may solve your problem.

---

### Post by SledgeHammer_999 on 2009-05-14
or make your main thread do the updating.(look [here](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-chapter-timeouts.html) for timeout functions)

---

### Post by C-- on 2009-05-18
Okay after some more work, the GUI updates when I mouseover it, but not on its own. I suspect this is because I am not calling the equivalent of a repaint() function, like in Swing. I cannot find anything in the gtkmm documentation that talks about this.

---

### Post by C-- on 2009-05-20
Okay Glib :: Dispatcher did the trick for updating labels. I just set the labels in another thread and then call dispatcher, which fires an event that triggers the GUI to update. You can also connect signal handlers to the dispatcher, however I do not bother with this is the handlers cannot be passed variable arguments.

As for the animation, I had to manually load the .gif into a Gdk :: PixbufAnimation and set it on the Gtk :: Image from glade with a call to Gtk :: Image :: set.

---

