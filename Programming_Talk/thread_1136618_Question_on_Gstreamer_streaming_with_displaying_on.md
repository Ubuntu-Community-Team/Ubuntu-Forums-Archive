---
title: "Question on Gstreamer streaming with displaying on the local computer"
date: 2009-04-25
forum: Programming Talk
---

### Post by KimHock on 2009-04-25
hello, i am new towards the ubuntu, gstreamer and python programming. i had a problem of unable to display my video on my computer when i transmit it using udpsink to another computer.
 
Another issues is that i will like to know more about how to configure the gstreamer in python programming so that i able to change the quality of the video that i streaming.
 
 
Maybe any one in here know any place that i can get the manual on all the function for Gstreamer in python to check how to configure video configure for the player/
 
thanks.
 
my code:
self.player = gst.parse_launch ("v4lsrc device=/dev/video0 !video/x-raw-yuv ,width=320,height=240 ! ffmpegcolorspace ! jpegenc ! multipartmux   !udpsink host= "+DestinationH+" port="+str(listenP)
 
Thanks alot. wish anyone around here can give me some advice....:)

---

### Post by SledgeHammer_999 on 2009-04-25
Documentation about Pygst is [here](http://pygstdocs.berlios.de/pygst-reference/index.html)

I don't know anything about streaming with gstreamer. For quality control I suggest to set the "quality" property of jpegenc(eg jpegenc quality=50), and maybe check the available properties for udpsink.

Note:
Use:
```
gst-inspect-0.10 *elementname*
```

in order to see what properties each element has.

---

### Post by KimHock on 2009-04-25
thanks alot for the reply. as i will look tru on tat part. I still wish those who know about the concurrently streaming and able to see the webcam video on the computer that is transmitting.
Thanks alot

---

### Post by KimHock on 2009-04-27
Thanks. i had find the solution for the display and sending problem.. using the tee command to assist the video.

---

