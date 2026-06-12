---
title: "gtkmm callback seg fault problem"
date: 2005-12-12
forum: Programming Talk
---

### Post by mdurham on 2005-12-12
Hi all,
I'm using gtkmm and have a problem with segmentation faults.
I have a group of  Gtk::ToggleButton(s), and from the handlers for the buttons I want to change the state of other buttons & maybe even the state of the button causing the callback signal.
This causes the aforementioned seg fault. I also have a display widget that is being constantly updated from an object run by a timer. This can also cause a seg fault if a callback coinsides with updating the widget.

It appears that I shouldn't update any widgets when one has produced a callback signal. Is that correct?
If any of that makes sense, what can I do about it? Any advice would be most welcome.

TIA Mike

---

