---
title: "c++ library for creating a greyscale image (draw squares)"
date: 2007-06-03
forum: Programming Talk
---

### Post by mallo on 2007-06-03
Hi,
I'm developing a c++ program for robotic purpose. The aim is to build a map of the environment based upon a quadtree data structure.
I made the first steps toward something that works  :D but I would like to build a visual output.
I think about a simple BMP or similar, or perhaps it could be nice a SVG.
My current output is a list of squares:
[ ex for a square ABCD: A(1,1) B(5,1) C(5,5) D(1,5)]
- I have a x,y coordinate of the lower-left corner [ex: A(1,1)]
- square edge length: [ex. 4]
- a float number, a probability: from 0 to 1. I'll map it in greyscale color like prob*(2^colour_depth)

I think that with a bmp library I need to use some for cycle, while a svg probably has the possibility to say something like draw_square(x,y,dim).

Anybody could give me some hint about which library to use?

Thanks ;)

---

### Post by kroiz on 2007-06-03
haven't used it but I think the most popular library for image manipulation is image magik.

---

### Post by nitro_n2o on 2007-06-03
you don't need an image library to draw grayscale squares, you can do this very easily as if you are writing to a file... look up the PPM image format it's very easy to use!!! 

ohh yeah quad trees are coool :) have fun

---

### Post by mallo on 2007-06-03
thanks  :).

I looked at PPM and Magick++...I think I'll use this library :).
It's very simple ^_^
[http://www.imagemagick.org/Magick++/Drawable.html](http://www.imagemagick.org/Magick++/Drawable.html)

with this command to compile
//c++ -o mag magick.cpp `Magick++-config --cppflags --cxxflags --ldflags --libs`


Bye ;)

---

