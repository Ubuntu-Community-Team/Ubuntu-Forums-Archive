---
title: "Video for Linux Two (V4l2)"
date: 2011-01-07
forum: Programming Talk
---

### Post by ierosvin on 2011-01-07
hi,

is anyone familiar with this interface? and knows how to capture video using this?

i tried to workaround things in [http://v4l2spec.bytesex.org/spec/a16706.htm](http://v4l2spec.bytesex.org/spec/a16706.htm) (capture.c), the example given in v4l2 spec, but it doesnt show how we could save the images captured to video.

i tried runnning the program as

```
 $ capture -o > file.mpeg
```and the resulting video plays really fast. im thinking this is not the right way to save it. :confused:

help please.

thanks!

---

### Post by skullmunky on 2011-01-07
Here's a code sample that will at least let you view an image, using v4l2 and SDL:

[http://ubuntuforums.org/showthread.php?t=1056663]("http://ubuntuforums.org/showthread.php?t=1056663")

I think the capture example as-is on the website just grabs frames but doesn't really do anything with them.  if you want to capture video, you probably want to encode on the fly using the ffmpeg libraries, or something more high-level like MLT.  

But I think the best way is the magic of GStreamer.

I just tried this out and it worked perfectly: 

```

gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! queue ! videorate ! 'video/x-raw-yuv,framerate=30/1' ! theoraenc ! queue ! oggmux ! filesink location=test.off

```

from this excellent tutorial 
[http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/]("http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/")

---

### Post by skullmunky on 2011-01-07
Here's a code sample that will at least let you view an image, using v4l2 and SDL:

[http://ubuntuforums.org/showthread.php?t=1056663]("http://ubuntuforums.org/showthread.php?t=1056663")

I think the capture example as-is on the website just grabs frames but doesn't really do anything with them.  if you want to capture video, you probably want to encode on the fly using the ffmpeg libraries, or something more high-level like MLT.  

But I think the best way is the magic of GStreamer.

I just tried this out and it worked perfectly: 

```

gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! queue ! videorate ! 'video/x-raw-yuv,framerate=30/1' ! theoraenc ! queue ! oggmux ! filesink location=test.off

```

from this excellent tutorial 
[http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/]("http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/")

---

### Post by skullmunky on 2011-01-07
Here's a code sample that will at least let you view an image, using v4l2 and SDL:

[http://ubuntuforums.org/showthread.php?t=1056663]("http://ubuntuforums.org/showthread.php?t=1056663")

I think the capture example as-is on the website just grabs frames but doesn't really do anything with them.  if you want to capture video, you probably want to encode on the fly using the ffmpeg libraries, or something more high-level like MLT.  

But I think the best way is the magic of GStreamer.

I just tried this out and it worked perfectly: 

```

gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! queue ! videorate ! 'video/x-raw-yuv,framerate=30/1' ! theoraenc ! queue ! oggmux ! filesink location=test.off

```

from this excellent tutorial 
[http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/]("http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/")

---

