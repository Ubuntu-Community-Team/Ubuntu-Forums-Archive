---
title: "can't detect minimize with unity and pygtk"
date: 2012-01-06
forum: Programming Talk
---

### Post by Brandon Williams on 2012-01-06
With gtk, it should be possible to determine when an application window is minimized and also whether an application window is minimized. With XFCE, LXDE, and Gnome2 (haven't tried Gnome3), this all works as expected: When the minimize button is clicked, a window-state-event fires which indicates that the ICONIFIED state has changed. When a window is already minimized, it is possible to use gtk.Widget.get_state() to determine that this is the case.

I recently started using Unity, and I noticed that a PyGtk application that I wrote does not receive a window-state-event when the window is minimized, and it also is does not indicate that the window is minimized in the return from gtk.Widget.get_state(). When the window is minimized due to a call to gtk.Window.iconify, no window-state-event fires, but it is possible to determine whether the window is minimized with gtk.Window.iconify_initially.

The application can be configured to use a status tray icon, and when the tray icon is in use, left click on the icon is meant to minimize/unminimize the window and the window is meant to be hidden from the launcher bar when minimized. With Unity, I can't figure out when to hide the launcher icon due to the missing window-state-event, and when the minimize button is used, it takes two status icon clicks to unminimize (first click erroneously calls iconify, second click correctly calls deiconify).

Does anyone know how to get reliable notification of minimize in pygtk when using Unity? and also how to determine whether the window is already minimized? Is there a way to make the existing mechanisms work correctly?

---

