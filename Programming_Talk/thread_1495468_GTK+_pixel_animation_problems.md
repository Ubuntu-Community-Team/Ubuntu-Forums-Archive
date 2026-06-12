---
title: "GTK+ pixel animation problems"
date: 2010-05-28
forum: Programming Talk
---

### Post by Mus1 on 2010-05-28
I want to draw an image on a window and change every single pixel one at a time.
The general alteration of the image works fine, but i can't update the image on the window after updating a single pixel.

I am using g_timeout_add() to call the function that changes the pixels once.
In the loop that iterates through every pixel i call gtk_main_iteration() to update my window.

That does not work.

What is the best approach to solve a problem like this?

---

