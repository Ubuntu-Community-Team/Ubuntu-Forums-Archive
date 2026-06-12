---
title: "Gtk::Scale mouse click issue"
date: 2012-09-06
forum: Programming Talk
---

### Post by bird1500 on 2012-09-06
Hi,

Gtk::Scale has settings that allow moving the slider by
1) page increment
2) step increment
3) dragging it

However, I need to make its slide jump to the location where a mouse click occurred, like in video and audio players, and none of the 3 solutions above works this way.

Listening to mouse events to adjust the value (the slider) manually - doesn't work, for some reason Gtk::Scale only reports double clicks.

Any solutions or workarounds?

---

### Post by bird1500 on 2012-09-07
I found that in Ubuntu 12.10 beta1 this issue is solved - the slider jumps to the location of the mouse click by default. I also googled & found a few bug reports on this issue marked as solved for Ubuntu 12.10, so I'll prolly move to 12.10 when beta 2 comes out.

---

