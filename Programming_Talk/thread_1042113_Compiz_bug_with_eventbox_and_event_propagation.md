---
title: "Compiz bug with eventbox and event propagation"
date: 2009-01-17
forum: Programming Talk
---

### Post by nandhp on 2009-01-17
I have a GTK program written in Perl with a label that turns into a slider when the mouse moves over it. It has worked fine with Metacity (and XFWM) for some time, but I just activated Compiz and it doesn't work: When running under Compiz, the slider never gets events.

Basically, I have an eventbox with a label inside, and set_above_child true. When the mouse enters the eventbox, the widget is switched to the slider. The user can then grab the slider control and use it normally. However, when using Compiz, the button-press and subsequent motion events are received by the box, not by the slider. I have attached a Perl program which demonstrates this problem.

This seems to be a bug, but I'm not sure if it's in Compiz, Gtk, my program, or somewhere else entirely. I also tried running the program under Metacity with the metacity compositor enabled, but the problem does not occur, so it seems to be compiz-specific.

I hope someone can point me in the right direction.

---

