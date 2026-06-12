---
title: "[PyGTK]handling keyboard input"
date: 2010-05-03
forum: Programming Talk
---

### Post by Jordanwb on 2010-05-03
I'm making a simple grid based game using PyGTK. What event would I need to connect to so I could catch and handle keyboard input such as the up, down, left and right arrows?

---

### Post by cdekter on 2010-05-04
key-press-event or key-release-event which originate from any object derived from gtk.Widget

---

### Post by Jordanwb on 2010-05-04
Thanks.

---

