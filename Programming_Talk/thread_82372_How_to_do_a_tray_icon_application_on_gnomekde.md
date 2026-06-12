---
title: "How to do a tray icon application on gnome/kde?"
date: 2005-10-26
forum: Programming Talk
---

### Post by jlist on 2005-10-26
On Windows, you can develop an application that shows an icon in the system tray area to save on screen space. If you right click on it, you'll get access to its functionality, for example, open its  GUI window, or about box, or exit. I wonder if there is a way to do this on gnome and kde?

---

### Post by Samuel on 2005-10-26
AllTray is a program that lets you send any window to a tray icon, to get it back you just click on the icon, i put the altray launcher next to the systray and when you click it the cursor turns to a crosshair and you click on one of your open windows to send it to the tray ```
sudo apt-get install alltray
```
hope this is what your looking for

---

### Post by mostwanted on 2005-10-26
[http://developer.gnome.org/doc/API/2.0/gtk/gtk-GtkStatusIcon.html](http://developer.gnome.org/doc/API/2.0/gtk/gtk-GtkStatusIcon.html)

---

### Post by jlist on 2005-10-26
Thank you both. I was looking to do it programmatically, so mostwanted's answer seems to be what I was looking for.

I wonder if it'll work on KDE, too?

---

