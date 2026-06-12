---
title: "C graphics in gcc"
date: 2010-03-08
forum: Programming Talk
---

### Post by utkarshjadhav on 2010-03-08
I dunno how to do C graphics programming in UBUNTU.
I am thinking to do my mini project in c graphics and that too in UBUNTU.
project is mostly a 2D .titled-multi-story parking system.
I am complete beginner to UBUNTU C grahics programming. plz temme how to do it..What files it requires..what additional packages are there....evey basic thing about C graphics programing in UBUNTU.
LINKs on how to do are also welcome.
please f1!!!!

---

### Post by Lux Perpetua on 2010-03-08
For 2D graphics, there are two very different routes you can take: (1) raster graphics and (2) vector graphics. Raster graphics is pixel-oriented, while vector graphics is shape-oriented. Anything you can do with raster graphics you can also do with vector graphics, and vice versa - but with difficulty, so choose carefully. If you plan to do anything with images (jpg, png, bmp, etc.) or pixel maps, then you probably want raster, whereas if you plan to work mainly with shapes (rectangles, circles, ellipses, lines, curves, etc.), in filled or outline form, then you probably want vector. 

These aren't the only options, but I'll recommend some packages to start: a good C raster graphics library is [SDL](http://www.libsdl.org/), and a good C vector graphics library is [Cairo](http://www.cairographics.org/). Both are in the Ubuntu repositories and are well documented on the web and have good examples/tutorials.

---

### Post by utkarshjadhav on 2010-03-10
useful one-------------


[http://www.openpeta.com/index.php/2d-graphics-using-c-in-linux-graphics-h-in-linux/comment-page-1/#comment-648](http://www.openpeta.com/index.php/2d-graphics-using-c-in-linux-graphics-h-in-linux/comment-page-1/#comment-648)

---

### Post by hyperAura on 2010-03-10
well i had a course on graphics about a year ago and we used the gtk toolkit along with c which was pretty simple and easy..

this link is to download the toolkit.. there u can also find documentation for every thing that u might need..

[http://www.gtk.org/download.html](http://www.gtk.org/download.html)

---

### Post by Eisenwinter on 2010-03-10
Another useful link is [http://google.com/](http://google.com/)

Search for "C graphics programming".

---

