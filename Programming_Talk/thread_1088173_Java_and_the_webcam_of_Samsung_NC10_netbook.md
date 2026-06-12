---
title: "Java and the webcam of Samsung NC10 netbook"
date: 2009-03-05
forum: Programming Talk
---

### Post by marce34 on 2009-03-05
Hi,

I have a Samsung NC10 netbook with a 1.3 MPixels webcam. I use it with windows in JMF with no problem, and would like to use it on Ubuntu.

The problem is that the jmfregistry application doesn't detect the camera, and hence i can't use it with JMF.

I tried the program Cheese which works ok with the camera, but another program that is based on video4linux gives an error.

The program that uses video4linux and can't connect to the camera is "motion". This is the output of the program:

```

[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3355136 LIBAVFORMAT_BUILD 3409664
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "Namuga 1.3M Webcam"
[1] cap.bus_info: "0000:00:1d.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0
[1] VIDIOC_S_INPUT: Device or resource busy
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Capture error calling vid_star 
```

Thanks in advance

---

### Post by leonox on 2009-04-29
Sun has not worked in Java Media Framework for around 6 years, for that reason I looked for another solution and I found OpenCV using java... here is a link with some details about this [http://walkintothefuture.blogspot.com/2009/04/opencv-java-linux.html]("http://walkintothefuture.blogspot.com/2009/04/opencv-java-linux.html").

---

