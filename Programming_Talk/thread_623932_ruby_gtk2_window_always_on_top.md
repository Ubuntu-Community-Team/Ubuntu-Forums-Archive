---
title: "ruby gtk2 window always on top"
date: 2007-11-26
forum: Programming Talk
---

### Post by allywilson on 2007-11-26
I'm developing just a little app for fun.

Basically, I'm using Ruby to open a gtk2 window with 3 buttons, one starts the webcam connected to the machine (/dev/video0), the other ends it and saves it to the desktop with a date_time name. The last button exits the application.

At the moment when the first button is clicked the video goes fullscreen. I'd like to keep this. But I would like the GTK window to stay on top. 

Does anyone know how to pass 'Always On Top'  to the window?

Any help appreciated :-)

---

### Post by MicahCarrick on 2007-11-27
Always on top of what? gtk_window_set_transient_for() will put a child window on top of a parent window and gtk_window_set_keep_above() will flag it to be on top, however, the window manager might not allow that. So that could vary depending on whether you're in GNOME, KDE, Windows, OSX, etc.

---

