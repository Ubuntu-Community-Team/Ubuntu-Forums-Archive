---
title: "[PyGTK] Drag-n-drop on systray icon"
date: 2010-10-20
forum: Programming Talk
---

### Post by spupy on 2010-10-20
I want to make a simple pygtk app that sits in the system tray and you can drop files on it. Unfortunately, I have not found a way to do this.
First I tried with the normal gtk.StatusIcon class. But it does not have the needed signals (drag_*). It inherits gobject, not the base widget class, that is the reason.

The python-eggtrayicon has another implementation of a systray icon. There is even some example of using drag-n-drop with eggtrayicon, but it doesn't work. The egg.trayicon.TrayIcon class does have the appropriate signals to handle drag-n-drop, but when I drop a file on it, nothing happens.
The exact same code that I use to connect the signals to the corresponding callbacks works flawlessly with a gtk.Window.

Any ideas how to enable drag-n-drop for a systray icon?

---

