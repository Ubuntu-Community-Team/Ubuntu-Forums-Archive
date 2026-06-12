---
title: "2D acceleration programming, c++"
date: 2009-04-21
forum: Programming Talk
---

### Post by terrax on 2009-04-21
Hello

I wonder how you could use the capability of 2d (or 3d acceleration) from you gfx card, for lets say, stream a video from you webcam.

If for an example I wan't to draw a frame from opencv (webcam capture lib) to a QImage (qt image object), I have to convert the CV image frame to a QImage format. But the webcam fetching / conversion / drawing to the screen is taking about 30 % cpu. Thats a lot for a C2D 2,5 GHz.

Is there any way I could do this conversion / showing via the GPU instead of the CPU? Or is there any other approach I could try?

---

