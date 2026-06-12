---
title: "[Gtkmm] Question about UPDATE_DELAYED"
date: 2010-02-19
forum: Programming Talk
---

### Post by kahumba on 2010-02-19
Hi,
I use the UPDATE_DELAYED policy for a Gtk::Range (the VScrollbar of a ScrolledWindow), this is how this policy works:
> 
Gtk::UPDATE_DELAYED - The *value_changed* signal is emitted when the user releases the mouse button, **or if the slider stops moving for a short period of time**.
Notice the bold words, can one change that short period of time?
In my case I badly need to make it shorter because otherwise the app feels sluggish.


ps: The other update policies aren't acceptable.

---

