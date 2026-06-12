---
title: "help me to make a very small change in an application"
date: 2009-11-03
forum: Programming Talk
---

### Post by medya on 2009-11-03
I use an application named gSTM , which is Gnome SSH Tunnel Manger,

when you hit on minimise it goes to tray and also remains in the taskbar ,

I want it to disappear from the taskbar too .

I have done programming in Windows a little , but never in ubuntu .
could someone tell me , where should I start to make this slight change in this application .

(I would also like to add a checkbox to remember my password)

---

### Post by Brandon Williams on 2009-11-04
I code for Gtk in python, not C, so I'm not sure about the exact syntax. I do have a method that works, though.

First, connect to 'window-state-event' for the main window. In the function that handles 'window-state-event', check the event's changed_mask and new_window_state values. If they both include WINDOW_STATE_ICONIFIED, then call hide on the main window.

Next, you may have to modify the code associated with the status tray icon in order to ensure that you call unhide on the main window if the main window is displayed again.

---

### Post by medya on 2009-11-04
in which environment do you do the editing ? is there a program like visual basic in ubuntu for GTK ? or an alternative

---

### Post by Brandon Williams on 2009-11-04
I use emacs.

But for those who want a full IDE, anjuta is the best that I've seen for Gtk and Gnome programming.
```
sudo aptitude install anjuta
```

---

