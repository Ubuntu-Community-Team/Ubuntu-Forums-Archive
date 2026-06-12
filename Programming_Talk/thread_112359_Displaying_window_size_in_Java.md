---
title: "Displaying window size in Java"
date: 2006-01-04
forum: Programming Talk
---

### Post by kaamos on 2006-01-04
Hello!

When gnome-terminal is resized, a small box appers that has the windows current size. I would like to use this feature in a small Java program, and I already have a usable listener for the windows size, but I'm at a loss how I would go about popping up such a box.

Ideas and suggestion are more than welcome. Thanks! :)

---

### Post by Viro on 2006-01-05
You could draw a white rectangle in the middle of the window, and write the window coordinates in the rectangle. You don't really need a box, just something to display the text, no?

---

