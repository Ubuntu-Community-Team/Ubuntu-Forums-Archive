---
title: "GTK+ fast image drawing"
date: 2015-09-12
forum: Programming Talk
---

### Post by theoryANDpractice on 2015-09-12
I want to have window with few buttons and one big image. Image should contain current object locations and they trajectory points. For this task, I use two GtkPixbuf and one GtkImage. I draw object locations into first pixbuf. When I should redraw image (several times per second), I copy first pixbuf to the second pixbuf, then draw current object locations on second pixbuf and finnaly copy second pixbuf to the GtkImage. Is there faster and optimal way to do this? Currently I use GTK+3. Thanks.

---

