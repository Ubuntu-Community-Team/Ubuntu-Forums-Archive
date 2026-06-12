---
title: "c++ - reading pixels from a file"
date: 2009-01-12
forum: Programming Talk
---

### Post by Despot Despondency on 2009-01-12
Hey, I want to write a program to read a file pixel by pixel, say a jpeg file, but not really sure how to go about it. Does c++ have the ability to do such a thing? Some pointers to related topics would be really appreciated. cheers

---

### Post by mike_g on 2009-01-12
It does, but I dont see why you would want to. Jpegs are one of the trickier image formats to decode, it would be much easier using a library like libjpeg, sdlimage, or magick wand.

If you want to learn how to decode image files yourself you would be best off studying an uncompressed format such as a bitmap. I wrote my own implementation in C once if thats of any use, you can find it [here](http://grundez.net/snippet.php?id=42).

Have fun.

---

### Post by efexD on 2009-01-12
You can but i highly reccomend you get a graphics library to read pixels. (SDL, SFML, Etc)

---

### Post by Despot Despondency on 2009-01-12
Hey, thanks for your responses. I'll have a look through those libraries.

---

