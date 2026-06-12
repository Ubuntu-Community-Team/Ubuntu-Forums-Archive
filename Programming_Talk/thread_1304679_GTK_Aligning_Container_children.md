---
title: "GTK Aligning Container children"
date: 2009-10-29
forum: Programming Talk
---

### Post by J V on 2009-10-29
I have a glade file (Suffice to say its really complicated) with a line of toggle buttons...

These buttons are not set to expand, because I want them to stay nice and square...

The problem with this being that the buttons are all at the left, and for purely aesthetic reasons I would like them to pack to the right (Or bottom if vertical)

How do I do this? (In glade please)

[IMG]http://i34.tinypic.com/fns3ec.png[/IMG]

---

### Post by Tony Flury on 2009-10-29
> **J V said:**
> I have a glade file (Suffice to say its really complicated) with a line of toggle buttons...

These buttons are not set to expand, because I want them to stay nice and square...

The problem with this being that the buttons are all at the left, and for purely aesthetic reasons I would like them to pack to the right (Or bottom if vertical)

How do I do this? (In glade please)

[IMG]http://i34.tinypic.com/fns3ec.png[/IMG]

In code - you would pack them at the end - and not at the start - not sure how you do that in Glade.

---

### Post by J V on 2009-10-29
Oh, I see the problem now, I was packing the Hbox rather than the contents, thanks for the help!

---

