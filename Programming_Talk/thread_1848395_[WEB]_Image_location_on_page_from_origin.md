---
title: "[WEB] Image location on page from origin"
date: 2011-09-22
forum: Programming Talk
---

### Post by Cousjava on 2011-09-22
I have a selection of partly transparent images, and I am looking for a way to display them, where they will be put together to forma composite image. The ones that will be included will vary, I will use PHP for changing which image will be used, and I understand how to create that bit. What I don't know is how to alter the location of the images. I have looked at margins but they alter the distance from the last element. How can I change where an image is displayed in relation to a point?

---

### Post by PaulM1985 on 2011-09-22
As far as I am aware you can't do this.  I don't think that you are able to overlay images (which I am assuming is what you are trying to do) using HTML.  I think the only way you can achieve this is to perform the overlay on the server to create one image, get the location of this new image, and then show it.

Paul

---

### Post by Peter76 on 2011-09-22
Read up on absolute positioning with css; that should do the trick.

Good luck

---

### Post by Cousjava on 2011-10-14
That was exactly what I wanted. Thanks!

---

