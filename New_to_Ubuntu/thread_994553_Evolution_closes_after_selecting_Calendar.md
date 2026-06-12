---
title: "Evolution closes after selecting Calendar"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by kelscmi on 2008-11-26
I am having the same problem with Evolution on my computer. Everything will work fine, but if I select "calendar" Evolution closes. The following is what I received when opening via the terminal.

```
(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Changing the queries (contains? "summary" "") 

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Segmentation fault
```

Does anyone have an idea on what:
1 caused the problem (yes decides user error)
2 how the problem can be resolved

Thank you in advance for your time.

---

### Post by amauk on 2008-11-26
do you use a Google calendar?

there's been a few bugs with evolution and google calendar integration lately

---

### Post by kelscmi on 2008-11-28
No, I don't use google calendar.  I have used the package manager to reinstall evolution again but still have the same problem.  When I open evolution via the terminal it will open up the calendar, but if I try to do anything it will close up.  If I open the program via the icon as soon as the calendar is selected it will close.
I have loaded Sunbird onto the computer.  Is it possible that it is causing the problem?

---

