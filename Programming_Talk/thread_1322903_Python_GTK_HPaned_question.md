---
title: "Python GTK HPaned question"
date: 2009-11-11
forum: Programming Talk
---

### Post by MeanEYE on 2009-11-11
Some time ago, in lack of any decent twin-panel file manager for Linux, I've started writing my own. Project is moving slowly but steadily :)

Anyway, since it's a twin-panel :) I have a slight problem in keeping aspect ratio between two panels. Sometimes out of no particular reason one of the panels gets bigger.

As I am quite new with Python and GTK+, am eager to know if there is a way of fixating panel aspect ratio. The goal is to keep panels at 50% (or any other %) of the window.

Just in case you are interested in how the whole thing looks at the moment I've attached a screen-shot.

Thanx!

---

### Post by Brandon Williams on 2009-11-11
From your screenshot, it looks like you have a GtkHPaned that has a GtkNotebook on each side. When I experiment with this in glade, it appears that when the two GtkNotebook objects are configured to Resize and not to Shrink, then the current aspect ratio is maintained. If the two GtkNotebook objects are equal in size, then as you expand the size of the window, both GtkNotebooks increase in size to maintain the 50/50 ratio. If on the other hand the two GtkNotebooks currently have a 30/70 ratio, then that is maintained as you expand the window.

If what you want is for them to _always_ be displayed with a 50/50 ratio, then you'll want to switch from a GtkHPaned to a GtkHBox.

---

### Post by MeanEYE on 2009-11-11
> **Brandon Williams said:**
> From your screenshot, it looks like you have a GtkHPaned that has a GtkNotebook on each side. When I experiment with this in glade, it appears that when the two GtkNotebook objects are configured to Resize and not to Shrink, then the current aspect ratio is maintained. If the two GtkNotebook objects are equal in size, then as you expand the size of the window, both GtkNotebooks increase in size to maintain the 50/50 ratio. If on the other hand the two GtkNotebooks currently have a 30/70 ratio, then that is maintained as you expand the window.

If what you want is for them to _always_ be displayed with a 50/50 ratio, then you'll want to switch from a GtkHPaned to a GtkHBox.
Hm I was thinking about that. But can I then add something like size grip to enable user to change the size of panels?

---

