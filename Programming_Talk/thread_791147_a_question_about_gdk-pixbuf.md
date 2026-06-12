---
title: "a question about gdk-pixbuf"
date: 2008-05-11
forum: Programming Talk
---

### Post by no1tom on 2008-05-11
Hi, every one,

I had question about gdk-pixbuf. I want to show some bmp files and I completed  the work by following steps:
1. create a pixbuf using *gdk_pixbuf_new_from_file() *
2. draw that pixbuf using *gdk_draw_pixbuf()*
it works fine, but I noticed that the bmp files all have background color (pink), and I want to hide it.

I know it has something to do with mask, but I don't which function show I use, could it be *gdk_pixbuf_render_threshold_alpha()*, or *gdk_pixbuf_render_pixmap_and_mask()*? and how to use it? Is there any one who can help me? many thanks!

---

