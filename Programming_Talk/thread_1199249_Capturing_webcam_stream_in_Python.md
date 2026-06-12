---
title: "Capturing webcam stream in Python"
date: 2009-06-28
forum: Programming Talk
---

### Post by antimatter15 on 2009-06-28
Hi, I'm experimenting with making a python script which handles webcam input. I've found [this]("http://www.jperla.com/blog/2007/09/26/capturing-frames-from-a-webcam-on-linux/") one that uses OpenCV to capture images. Sadly, it doesn't seem to work for me.

Running it gives
```
antimatter15@antimatter15-desktop:~/Desktop/mirrortouch$ python webcam2.pyTraceback (most recent call last):
  File "webcam2.py", line 29, in <module>
    im = get_image()
  File "webcam2.py", line 14, in get_image
    im = opencv.cvGetMat(im)
  File "/var/lib/python-support/python2.6/opencv/cv.py", line 3826, in cvGetMat
    return _cv.cvGetMat(*args)
RuntimeError:  openCV Error:
        Status=Null pointer
        function name=cvGetMat
        error message=NULL array pointer is passed
        file_name=cxarray.cpp
        line=2780

```

I'm not certain if it's related to this, but running v4l-conf shows
```
antimatter15@antimatter15-desktop:~/Desktop/mirrortouch$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 2880x1200, depth=24, bpp=32, bpl=11520, base=unknown
/dev/video0 [v4l2]: no overlay support

```
Which I've seen in other posts, but I can't find any way to fix it.

Does anyone know how to either fix this or know another way to capturing frames from a webcam in python?

---

### Post by soltanis on 2009-06-29
I don't know for certain but this is probably v4l messing up, not necessarily OpenCV or your program. I get that error too whenever I try to test my webcam, and it only ever works with Skype and xawtv (and NEVER with anything else).

Do you have one of the Ricoh webcams (like I do)? These are very poorly supported by the UVC driver, for some reason, and there is a kernel module driver for it, but it's old and unmaintained, then there's a newer userspace driver for it which is new and doesn't always work, so as is usual you get the pick of the old buggy driver or the new unfinished driver.

Or you might have another unsupported cam, in any case, you'd be better off asking about this in the hardware support forum, since I'm pretty sure its your webcam.

As far as I know there is no other way to get webcam streams other than v4l or v4l2.

---

### Post by loell on 2009-06-29
have you tried python gstreamer yet?

[http://giss.tv/sahabuntu/doc/gstreamer-v4l.html]("http://giss.tv/sahabuntu/doc/gstreamer-v4l.html")

---

### Post by antimatter15 on 2009-06-29
I don't understand how to process the individual frame snapshots with GStreamer.

I have a Creative NX.

---

