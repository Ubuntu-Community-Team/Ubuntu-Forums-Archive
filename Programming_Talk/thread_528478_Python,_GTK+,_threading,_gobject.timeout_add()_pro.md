---
title: "Python, GTK+, threading, gobject.timeout_add() problem"
date: 2007-08-17
forum: Programming Talk
---

### Post by Moses Palmér on 2007-08-17
Hello everyone,

I have written an application using Python/GTK+ to periodically check an RSS feed, and if it has been updated since the last check, download an image. The program displays an animated ticker (which is an SVG image rotated) while the update is in progress.

The first version supported only one simultaneous window. This was easily solved by doing the checking and downloading from a thread, and then use gobject.idle_add(...) to call the updating function from the main thread.

However, the new version of my program supports any number of windows, and now it doesn't really work at all---I get the infamous "Xlib: unexpected async reply (sequence 0x????)!" error. If I don't activate the ticker---if I don't call gobject.timout_add(...)---the program works, but I don't want to sacrifice this functionality, since it really adds to the user experience.

Has anyone had a similar problem---combining threads and gobject_timeout_add(...), I gather---and solved it?

---

### Post by Moses Palmér on 2007-08-17
I should add that there actually is no problem to add new windows to the application manually, but if I close it with more that one window open---it saves the configuration of all remaining windows upon termination---it crashes the next time I start it. I suppose this is caused by all windows trying to update at the same time.

The work done when the download is complete is pretty heavy: first it creates a new transparent gtk.gdk.Pixmap reflecting the new size of the window, then uses Cairo to render a frame and draw the downloaded image, and, depending on the configuration and the presence of a compositing window manager, draws a soft shadow by repeatedly filling a mask created by the frame and image with a semi-transparent colour rotated around an offset point and then finally sets the pixmap as the background of the window, resizes it and repositions some widgets.

---

