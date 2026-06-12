---
title: "best library to capture video inside C++"
date: 2012-05-09
forum: Programming Talk
---

### Post by mennowo on 2012-05-09
Hello,

currently I am working on an application inside [Openframeworks]("http://www.openframeworks.cc"). It is nice, among other things cause it provides for ready to use classes for doing things like capturing video, displaying things on the screen, etc.

However, I run into trouble using multiple cams inside Ubuntu 12.04 64 bits. I am using 2 ps3 cameras: they are capable of capturing 640x480 at 60fps, which does however occupy all bandwith of the used USB hub (per cam). 

Using Guvcview, which is based on V4L2 things run really fine using 2 cams, one at 60 fps, one at 30 fps (both at 60 fps I get "Could not grab image (select timeout): Resource temporarily unavailable").

Openframeworks depends on Gstreamer. I experience several issues here (also when using the tool 'cheese'):
- cams are only able to initialize when connected to certain usb ports. Eg. not when connected to my Belkin USB2.0 pci card (which works fine with Guvcview).
- I cannot capture from 2 ps3 eye cams simultaneously. However, it does work to capture from 1 ps3 eye and one small Logitec cam.
- At some point I got an app running with two cams, howeverthe images were flickering and either the one or the other of the cams got updated, while the other halted
- At some point I got things working at 30 fps for both cams, but it was unstable and I got lots of seg faults after small changes to the program, the reason for which I couldn't find...

Overall this seems very (too) unstable for my purposes. I am wondering: is V4L2 a better option than Gstreamer? If so, does [this example]("http://v4l2spec.bytesex.org/spec/capture-example.html") still provide me with relevant information as to how to implement V4L2 inside my C++ application? I would guess the V4L2 API has changed and been updated since 2007? SO maybe there are better ways than shown in the example. Or maybe the interface has remained stable and hter have just been internal changes...
I have not found any C++ class/wrapper for V4L2. I am hoping that writing a small class around this will allow me to initialise multiple cams...

What I need: load image data into an unsigned char * array. Also, best would be if I can change camera settings, like resolution, brightness, contrast, etc, from within the code (like what is possible inside Guvcview...).

Actually I'm quite a beginner still where implementation of libraries and APIs inside my own programs is concerned. Hope to find some pointers in the right direction here :-).

Any help really appreciated, Menno.

---

### Post by mennowo on 2012-05-18
Meanwhile I solved this issue. I used the example code for V4L2 mentioned in the previous post and built a small C++ class out of it, for use inside OpenFrameworks. I think it can easily be adjusted to be used in other frameworks that use C++.

See here for the code: [https://github.com/mennowo/ofxV4L2](https://github.com/mennowo/ofxV4L2).

Any comments, feedback, etc, are of course welcome!

---

