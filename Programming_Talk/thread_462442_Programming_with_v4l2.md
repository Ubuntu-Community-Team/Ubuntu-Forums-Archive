---
title: "Programming with v4l2"
date: 2007-06-02
forum: Programming Talk
---

### Post by diego_sza on 2007-06-02
Hi, I'm trying to write a simple program to capture video from a pinnacle card (bttv driver). I followed the steps of the v4l2 api documentation and everything's fine. I've got communication with the device, and apparently it is capturing video.
The problem is, I don't know how to bind it with an X window.
I haven't found good documentation for doing that. I also tried to find documentation about the Xv extension but what I got is not enough.

Thanks.

---

### Post by wkulecz on 2007-06-05
Try:

 [http://www.ferzkopp.net/joomla/content/view/13/14/](http://www.ferzkopp.net/joomla/content/view/13/14/)

While libbgrab is V4L based, it works with V4L2 using the compatability layer.  You can probably ignore libbgrab but look at the included xutil library and the example programs to see how to do color depth conversions, and text overlays on the video.

Saved me a bunch of time,  I sent the author a few minor changes to use V4L2 ioctrls to probe for the input mapping as that assumed in libbgrab was not right for my hardware, and a change to xutil to trap X-window close events so I could clean up properly if the user closed the video window instead of using my close control, but  I don't think he's updated the package in a long time.

Personally I think V4L2 is way more complicated than necessary because of its be all do all approach.  Instead of doing something simple like: error=SetVideoCaptureMode( NTSC, 640,480, 8_BIT_MONOCHROME);  you have to make a bunch of calls to "enumerate" hardware features and try to figure out if the hardware does what you need, and then make the appropriate calls to setup the options correctly.

--wally.

---

