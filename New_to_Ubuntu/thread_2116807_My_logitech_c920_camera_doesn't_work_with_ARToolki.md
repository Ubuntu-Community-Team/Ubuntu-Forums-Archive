---
title: "My logitech c920 camera doesn't work with ARToolkit(In Ubuntu 12.04 x86_64)"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by farrington on 2013-02-16
[B]My embedded Toshiba c855-s5206 web camera works fine with ARToolkit  2.72.1  . But I'm having trouble in making the "simpleTest" run with my  Logitech c920 webcam. I get the following error when I run the  ./simpleTest woth the Logithech c920 webcam:
 
Using config string from environment [v4l2src device=/dev/video0 ! image/        
                     jpeg,width=1920,height=1080,framerate=15/1,rate=15 ! queue ! jpegdec ! queue ! ffmpegcolorspace !     
                     identity name=artoolkit ! fakesink].
                     libARvideo: GStreamer 0.10.36
                     libARvideo: GStreamer pipeline is PAUSED!
                     libARvideo: GStreamer negotiated 1920x1080
                     libARvideo: GStreamer pipeline is PLAYING!
                     libARvideo: GStreamer pipeline is PAUSED!
                     Image size (x,y) = (1920,1080)
                     *** Camera Parameter ***
                     --------------------------------------
                     SIZE = 1920, 1080
                     Distortion factor = 955.500000 790.500000 2.911111 1.012757
                     2102.85441 0.00000 949.50000 0.00000 
                      0.00000 2178.28254 724.50000 0.00000 
                     0.00000 0.00000 1.00000 0.00000 
                     --------------------------------------
                     libARvideo: GStreamer pipeline is PLAYING!
                     Segmentation fault (core dumped)
 
The camera works fine with Gstreamer but I get this error with any  binary I run from the examples of ARToolkit. Additionally, I tried to  lower the resolution and frame rate of the camera by changing the  "width=1920,height=1080,framerate=15/1,rate=15" with lower values.
 
Do you guys have any idea what's going on??                         [/B]

---

