---
title: "[gtkmm/gtk]How to be notified about a window resize?"
date: 2009-03-19
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-03-19
I want to be notified each time the user resizes the window. The closest signal I found is the "signal_size_allocate" (from the widget class). But I ran into some problems:

1.The signal is emited even when my code resizes the window. So is there a way to distinguish when the *user* resizes it?

2.The signal is emited even when a button(on that window) is clicked. Even though the window's dimensions don't change. Why is that happening? How to know when the window has actually changed sized?

or is there some other way/signal to be notified for a resize of a specific widget?

---

### Post by Marco A on 2009-03-19
.

---

### Post by cabalas on 2009-03-19
As to the second question I found this in the docs about size allocate - This function is only used by Gtk::Container subclasses, to assign a size and position to their child widgets. - I would take that to mean that whenever a child widget has it's size changed that the signal will be fired.

Distinguishing between user resize and programmatic resizing I would just use a bool set it to true when you resize the window and when the signal handler is called set it back to false but don't do what you want to do when a user resizes the window.

While it would seem that signal_size_allocate may not be what you are after have you tried catching either signal_size_request (a signal in the widget class) or signal_check_resize (a signal in the container class) both I believe fire when the window is resized.

---

### Post by hessiess on 2009-03-20
> **Marco A said:**
> When the user resizes the window a mouse click must occur, followed by the mouse button release.

You could just update the window size in the button-press-event.

 Then check if the size changed in button-release-event.

Not neseserraly, Tiling Window Managers are keyboard controlled and automatically resize windows based on what other windows are open. for example.

---

### Post by SledgeHammer_999 on 2009-03-20
> **cabalas said:**
> As to the second question I found this in the docs about size allocate - This function is only used by Gtk::Container subclasses, to assign a size and position to their child widgets. - I would take that to mean that whenever a child widget has it's size changed that the signal will be fired.

Distinguishing between user resize and programmatic resizing I would just use a bool set it to true when you resize the window and when the signal handler is called set it back to false but don't do what you want to do when a user resizes the window.

While it would seem that signal_size_allocate may not be what you are after have you tried catching either signal_size_request (a signal in the widget class) or signal_check_resize (a signal in the container class) both I believe fire when the window is resized.

Thank you all because you gave me some ideas how to solve it.

@cabalas signal_size_request and signal_check_resize behave the same way. These signals are emitted even when a button is clicked(one for the pressed state and one for the released state).

I solve it this way. I've set up 2 int vars in my class. Each time I want to resize I first update these vars with the intended size and then I do the resize. Then the signal is emitted. My callback checks if the delivered size is different than my vars. if it is it continues, otherwise it ends without doing something. The bad thing about this, is that my callback will be called even when a button is clicked, which isn't necessary. For the moment it works.

---

