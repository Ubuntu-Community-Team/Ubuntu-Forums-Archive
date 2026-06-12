---
title: "GTK+ Image"
date: 2009-12-22
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-22
I have been using gtk_image_new_from_file () in my GTK+ C Programs to display images.  After I load the image in, I pack it into a table usually to position it.  How can I display an image on top of another image?

---

### Post by bruce89 on 2009-12-22
You'd have to do a custom widget and draw the two images into it. Either that or use GtkFixed (which is not a good idea).

---

### Post by lewisforlife on 2009-12-22
I was thinking about making a board game on the computer.  I was thinking the board would be an image, and the game pieces would move on top of that image.  How would you go about doing that?

---

### Post by qalimas on 2009-12-22
> **lewisforlife said:**
> I was thinking about making a board game on the computer.  I was thinking the board would be an image, and the game pieces would move on top of that image.  How would you go about doing that?

I've been fighting that with Ruby and Glade ._.

From what I read, but do not understand yet, is you need to make a canvas, then draw the images on top of it (it acts as a sort of imaqge container if I'm not mistaken).

I hope that is valid information, if anything it will help you out on Google :lolflag:

---

