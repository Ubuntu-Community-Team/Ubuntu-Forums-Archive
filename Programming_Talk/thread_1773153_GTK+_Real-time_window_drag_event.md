---
title: "GTK+ Real-time window drag event?"
date: 2011-06-01
forum: Programming Talk
---

### Post by Githlar on 2011-06-01
I have two windows in my program, one directly overlaying the other. The top window has a border, the bottom window doesn't. However, I would like to be able to move these windows in unison so that they appear to be a single window. First, I tried using the configure-event callback, but the bottom window is not re-placed until the the upper window is in it's new position (mouse button released). As of now it looks really bad, when you drag the window to move it, it appears that only the frame moves (as the internals are transparent) until you release the mouse button and the other window is re-placed under it.

Is there any way in standard GTK+ to achieve this task?

---

### Post by Githlar on 2011-06-02
Bump?

---

