---
title: "[Gtk] DrawingArea repaint strategy"
date: 2012-08-20
forum: Programming Talk
---

### Post by t1497f35 on 2012-08-20
Hi,
I have a Gtk::DrawingArea inside a scrolled window.

After creation of both widgets I (use cairo to) draw the whole area of my Gtk::DrawingArea but then while scrolling down this widget below the initial visible area it appears all gray so I have to keep redrawing parts of it - again!

Question - how do I avoid it so that I don't have to keep repainting it while scrolling?

---

