---
title: "Noob-ish Glade Question"
date: 2009-10-10
forum: Programming Talk
---

### Post by M4rotku on 2009-10-10
Hey Guys,

I'm running into a bit of a problem.  I am rewriting a glade file that was in libglade into gtkbuilder.  I need to set the default of a GtkSpinButton to 1.  In libglade, setting the default number was obvious, but in gtkbuilder, I looked everywhere and can't find it.  Is GtkSpinBuilder now used for more than just numbers? 'cause now it has a bunch of settings for icon stuff.

I'm hoping that this will be an easy question:  How do I change the default number from 0 to 1?

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-10-11
bump

---

### Post by steeleyuk on 2009-10-11
I think you need to use GTK Adjustment. You can set minimum/maximum values, step values and a bunch of other things. Then link it to the spin button.

In Glade 3.6.7, the SpinButton Adjustment button is located below the text entry to name the widget.

---

### Post by M4rotku on 2009-10-12
Thanks, does this change how i will have to connect my signals?  I need it to send a signal when changed so that I can add some extra rows and such.

---

