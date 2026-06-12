---
title: "V4L help or altternative"
date: 2009-01-05
forum: Programming Talk
---

### Post by 2weird on 2009-01-05
Hello and Happy New Year to all.

Excuse me (and correct me) if I am posting in the wrong forum.
I would like to know one of two things regarding v4l (both would be much appreciated).

1) What is the simplest way to grab an image in C using the V4L libraries directly and storing the image in an array of structs that store the rgb values. I have tried reading the tutorial by Alan Cox and even looked at some source code (google capture.c) and none have shown a simple way of grabbing an image and storing the data in an array.

2)Is there an external library that can do the above for me.

Thank you for your help.

---

### Post by 2weird on 2009-01-05
On second thought, I would like to restate my question differently.

What is the simplest way (without any error handling and other fluff) to just capture an image in C and store it as an image (any format will do for now). I just want to learn which commands do this work because I am having a hard time understanding examples out there and I am not exactly a programming pro.

Thank you in advance.

---

### Post by mike_g on 2009-01-05
Never heard of V4L before, but you could try [Magick Wand](http://www.imagemagick.org/script/magick-wand.php) with Image Magick. SDL with SDLImage is another relatively easy option.

---

### Post by 2weird on 2009-01-05
V4L is short for Video 4 Linux. =P
So by getting an image I mean getting an image from a video device ( in my case a web cam).

So, I want know how to capture a single frame from my webcam and then store that as an image.

---

### Post by skullmunky on 2009-01-07
Hi, 

I think I know what you're asking, which is, why is it so hard to find a simple demo app for V4L that works? :)  I ran into the same problem and finally did get something put together, capturing from V4L and displaying using SDL.  Unfortunately it's on a computer in another state, so if you don't get anything working in the next couple weeks pm me with a reminder and I'll post it.  None of the example/tutorial code I could find anywhere worked at all, which I think is partly because there's a difference between V4L 1 and V4L 2.  

Another way that's a little easier than using straight V4L is to use a higher level wrapper library.  I've had good luck with the PortVideo library:

[http://mtg.upf.es/reactable/?portvideo](http://mtg.upf.es/reactable/?portvideo)

which is part of the ReacTable project.

[http://mtg.upf.es/reactable/?software](http://mtg.upf.es/reactable/?software)

---

