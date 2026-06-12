---
title: "Gtk::DrawingArea repaint issue"
date: 2010-12-31
forum: Programming Talk
---

### Post by t1497f35 on 2010-12-31
Hi folks,
Have a look at the screenshot. My little file browser uses a Gtk::DrawingArea and Cairo to paint the files names and anything else you see in the center area.
But when I move a window of another app over the window of my app the DrawingArea doesn't seem to receive any sort of "repaint" signal so the painting gets scrambled as seen on screenshot.
Any idea why? Do I need some other notification from the system besides the "on_expose_event" one?

EDIT: also attached a screenshot of how it should look.

---

