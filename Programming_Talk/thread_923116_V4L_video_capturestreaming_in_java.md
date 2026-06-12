---
title: "V4L video capture/streaming in java"
date: 2008-09-18
forum: Programming Talk
---

### Post by djails on 2008-09-18
Hi,
I have written a GPL'd java package called Video4Linux4Java, v4l4j in short. It is a simple API that captures images from any V4L video devices such as webcams, capture cards and TV-tuner cards. v4l4j grabs the images from the device, JPEG-encodes them and hands them out encapsulated in Bytebuffer objects. v4l4j also makes all the video controls available (including those private ioctls some drivers still implements !). 
It is really easy to use, and works great. It comes with 2 sample apps, one that shows the maximum achievable fps and the other displays the video stream in a window (JFrame). There is another C application that sends multipart-JPEG streams to <img> tags of web browsers (doesnt require a java applet). I have tested it with several devices including USB webcams, and bttv-based capture cards.
I hope it will benefit someone. If you try it out, please take a couple of minutes to give me some feedback on what's missing, what's working/not, ...
Here is the project url:
[http://v4l4j.googlecode.com]("http://v4l4j.googlecode.com")

---

