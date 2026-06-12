---
title: "Pygtk gtk.combobox only emits signal on &quot;expose&quot; event.  How to capture other events?"
date: 2008-02-06
forum: Programming Talk
---

### Post by megadave on 2008-02-06
Hi all,

I occasionally work on a side project of mine; improving my workout tracking program..  It's written in python and uses pygtk for the gui.

Anyway, what I'm trying to do now is improve the UI usability.  In my template table, I want to catch ideally an "enter" event, or at least a button_press event when the user enters the combo box in the next row, so that I can pre-scroll it to the previous option, to save time.

So you're putting in your workout, you go to the next line and

[IMG]http://img115.imageshack.us/img115/3285/template1bt9.png[/IMG]



you're met with this



[IMG]http://img115.imageshack.us/img115/5961/template2xx1.png[/IMG]

I'd rather have the option pre-selected to save the user (me and my gf) time.

```

self.combo_exercise.set_events(gtk.gdk.ALL_EVENTS_MASK)
self.combo_exercise.connect("focus_in_event", self.cb_combo_exercise_enter_event, self.combo_exercise)

```

The only event it triggers on is the "expose" event.  I'd be happy w/ an enter, in_focus or button press.  This can't be a missing feature.  Anybody have any ideas.

Thanks

---

