---
title: "[SOLVED] [pygtk]How to use multiple windows?"
date: 2008-07-25
forum: Programming Talk
---

### Post by days_of_ruin on 2008-07-25
I am using glade and to make my second window popup I "show_all" on the
second window to make it appear.I then close it and press the button
that made it appear again only now its an empty window filled with
gray.

What is the correct way to use multiple windows?

---

### Post by Quikee on 2008-07-26
> **days_of_ruin said:**
> I am using glade and to make my second window popup I "show_all" on the
second window to make it appear.I then close it and press the button
that made it appear again only now its an empty window filled with
gray.

What is the correct way to use multiple windows?

Don't allow that the second window is closed - hide it instead. When you press the button again - just show again.

---

### Post by days_of_ruin on 2008-07-26
> **Quikee said:**
> Don't allow that the second window is closed - hide it instead. When you press the button again - just show again.

I tried that.Still doesn't work.

EDIT:btw I had the "hide_all()" call in the windows destroy callback.
But it destroys the window anyway.

---

### Post by days_of_ruin on 2008-07-26
solved.In the button to create the second window I made the gtk builder
load the xml file again and then get the window again.

---

