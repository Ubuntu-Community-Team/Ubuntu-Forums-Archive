---
title: "GTK window positions not working"
date: 2008-09-01
forum: Programming Talk
---

### Post by HyperHacker on 2008-09-01
I'm finding two oddities trying to save and restore window positions. First, gtk_window_get_position() is always giving me 0,0 (but gtk_window_get_size() works). Second, gtk_window_move() was working before I reinstalled Xubuntu, but now it seems to think my left monitor (which is the primary X screen set in nvidia-settings) doesn't exist; if I try to move a window into it (any X position < 1680), it just moves to the left edge of the right monitor. I can drag the windows over there myself, but gtk_window_move() won't put them there.

---

