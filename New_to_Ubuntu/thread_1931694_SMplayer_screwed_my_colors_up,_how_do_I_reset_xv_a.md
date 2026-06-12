---
title: "SMplayer screwed my colors up, how do I reset xv attributes?"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Huzudra on 2012-02-26
Hi, I foolishly messed with the video equalizer in SMplayer. The settings have stuck and I can't clear them now. I need to use the intel buffered overlay to stop video tearing, but the contrast and colors are so out of whack its unwatchable. 

> owner@owner-Inspiron-6000:~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 3
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 131)
      "XV_SYNC_TO_VBLANK" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
  Adaptor #1: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 89
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 11
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is -19)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 127)
      "XV_SATURATION" (range 0 to 1023)
              client settable attribute
              client gettable attribute (current value is 146)
      "XV_PIPE" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is -1)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 526344)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 12632256)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)


So, as you can see the settings are messed up. How do I set them back?  I tried something in command line but it made no effect. 


xvattr -a XV_BRIGHTNESS -v 0 
xvattr -a XV_CONTRAST -v 0 
xvattr -a XV_SATURATION -v 0 
xvattr -a XV_HUE -v 0 


I did those, no change when I play a file or check xvinfo again, even tried sudo with those, no change either!  How do I set it back?

---

### Post by Huzudra on 2012-02-26
Ok, I tried the above commands again but with the -p for port and seem to have made the settings stay stuck changed....except now choosing intel video overlay in smplayer gives me a black screen. Yay, I made it worse!

---

### Post by Huzudra on 2012-02-26
I guess I fixed it. I don't know how. I rebooted once last night after making this thread, problem still persisted. I shut it down for the night, slept, woke up this morning and voila it works fine. Not a clue why or how either, but it works. I guess sometimes sleeping on it really does work. Or mentally threatening a clean install.

---

