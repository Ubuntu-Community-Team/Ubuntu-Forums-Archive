---
title: "Question about Cairo and Opengl"
date: 2008-10-30
forum: Programming Talk
---

### Post by di3go on 2008-10-30
I have some question, whats the main difference from cairo and opengl?

I need make a application with charts and my friends say to use cairo, i dont know really the main advance to use cairo instead of opengl, cairo has a backend glitz that use hardware acceleration and opengl is native hardware accelerated, im confused.... need some help ^^

Thanks!

---

### Post by kknd on 2008-10-30
You can draw using both, but cairo is optimized (not in the sense of performance, but functionality) for 2D drawing, while openGL has much more features (also used to model 3D environments, can handle cameras etc. It would be very unusual to find a program that uses opengl only for charts)

Also, cairo support more backends by default (this is important, as you don't specified what will be your output, like an image, or a drawing on top of a GUI widget).

---

### Post by di3go on 2008-10-30
The output is images, like gnome-system-monitor, i need it animated and in real time, but i found cairo kind slow, when i put the refresh rate to 0.25sec it consumes like 30% of my cpu i dont know if is a bug here or if can be optmized with glitz or something like this... 

I don't need 3d things, just cute and animated 2d graphics and interface

---

### Post by di3go on 2008-10-31
Anyone have any experience with Glitz? How fast is compared with Opengl?

---

### Post by kknd on 2008-10-31
Cairo focus is on quality, but it isn't slow (but I agree that gnome-system-monitor charts are really slow).

---

