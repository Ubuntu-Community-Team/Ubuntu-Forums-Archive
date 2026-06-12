---
title: "error: pkg-config --cflags opencv: no such file or directory"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by shikshasmurthy on 2014-01-02
i am getting this error when i included opencv headers to video_demo part of ar.drone_sdk to display video in opencv format..

wat should i do?

---

### Post by steeldriver on 2014-01-02
Hello and welcome to the forums

It would be easier to help you if you included a bit more information in your post - like the exact command and the exact error (you can cut+paste)

However, at a guess you have likely used single quotes instead of backticks around the pkg-config command - it needs to look like

```
**`**pkg-config --cflags opencv**`**
```
NOT
```
[COLOR=#ff0000]'[/COLOR]pkg-config --cflags opencv[COLOR=#ff0000]'[/COLOR]
```

On a US keyboard, the backtick is on the same key as ~

---

### Post by shikshasmurthy on 2014-01-02
thanks a lot for the reply..
that error is removed..
i have followed the instructions in petrkout.com/linux/parrot-ardrone-2-0-video-streaming-through-opencv-in-linux/ to get video stream through ar.drone using opencv.
but i am still getting few errors..could u please help me..i ll attach the make errors below:

In file included from /home/parrotuav/Documents/AR.Drone/ARDrone_SDK_2_0_1/Examples/Linux/video_demo/Build/../Sources/Video/display_stage.c:19:0:
/home/parrotuav/Documents/AR.Drone/ARDrone_SDK_2_0_1/Examples/Linux/video_demo/Build/../Sources/Video/display_stage.h:9:44: fatal error: ardrone_tool/Video/video_stage.h: No such file or directory
compilation terminated.
make[4]: *** [../../Soft/Build/targets_versions/linux_video_demo_PROD_MODE_vlib_Linux_3.5.0-44-generic_GNU_Linux_usrbingcc_4.6.3/Video/display_stage.o] Error 1
make[3]: *** [all] Error 2
make[2]: *** [build_app] Error 2
make[1]: *** [linux_video_demo] Error 2
make[1]: Leaving directory `/home/parrotuav/Documents/AR.Drone/ARDrone_SDK_2_0_1/Examples/Linux/video_demo/Build'
make: *** [all] Error 2

---

