---
title: "Scaling Image to fit parent widget (gtk)"
date: 2009-07-03
forum: Programming Talk
---

### Post by jediborger on 2009-07-03
I am writing a pygtk program which displays an image in a section. It is a picture directory program, so I have a person's info on the right and I want to display a picture of them on the left.

What I need is a way to have the picture scale to fit the parent widgets size. Currently when I load the pixbuf, it is way too large and takes over the screen. I can manually scale it but that impractical as every image in the database will have different dimensions. I'm hoping somebody out here has found a solution to this, either through a combination of gtk widgets or some little snippet of code that can do this image scaling for me. I would like the image to fill the space given and nothing more and resize itself when the window size has changed. Any ideas?

I have created the gui in glade using gtkbuilder and the image is loaded as a gdk.pixbuf if that helps anyone.

---

### Post by smartbei on 2009-07-03
You can scale images in bulk using any of [irfanview for windows or squash, gimp for linux]. Or, you can use a python image library such as python-imaging.

---

### Post by jediborger on 2009-07-03
I think you've missed my point. I don't want to manually scale these pictures. I am writing a graphical program in which I would like to display a picture in a part of it, and I would like it to fill the space given and resize itself when the window size changes. Much like how buttons change their size and so forth when you enlarge a window.

---

### Post by monraaf on 2009-07-03
I don't think images can automatically resize to fit parent width, you'll have to scale them yourself. You can use the pixbuf scale method for that.

[http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--scale](http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--scale)

---

