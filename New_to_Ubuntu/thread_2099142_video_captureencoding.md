---
title: "video capture/encoding"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by squakie on 2012-12-28
I have a Roxio USB video capture device that I've noticed some posts on the net for, but I was wondering:

- are there any GUI'd apps that will capture from this device, let me modify frame rates, quality, etc. and create an ISO or at least something with options other than mpeg4?  Cheese won't work - I have an internal video capture card and it won't let me change to another device for input.

- if not, not knowing anything about video encoding, so I'm thinking of trying something like writing an app that basically uses something like ffmpeg or a similar tool as a back-end.  Does anyone know if there is a way to programmatically get back the percentage completed, etc., from ffmpeg so I can display a status bar?

- just noticed VLC has a capture mode and I can select the device there for input.  I'm going to try that later tonight after I get done with some other things I need to do.

---

### Post by robertthebruce on 2012-12-28
Hi Squakie,

i presume youv'e tried zoneminder, it has a filter that you may be able to generate an iso from... 

i have got it running across several different machines
i usually install 12.04 server then get zm running and then install desktop

---

### Post by FakeOutdoorsman on 2012-12-28
I'm guessing that it may act like a webcam, and if that is true you can use the Video4Linux2 input video device in ffmpeg. Assuming the device is "/dev/video0", a simple test would be:

```
ffplay -f video4linux2 -i /dev/video0
```

ffplay is a simple player and it should be able to play the video stream from the device if successful.

You can get more information about the device with:
```
ffmpeg -f video4linux2 -list_formats all -i /dev/video0
```
or
```
v4l2-ctl --list-formats-ext
```

Then you can capture with ffmpeg. This is just an example, but may not work with your device:
```
ffmpeg -f video4linux2 -framerate 30 -video_size hd720 -i /dev/video0 -c:v libx264 -crf 23 output.mp4
```

Note that my commands will work with ffmpeg from FFmpeg, but probably won't work with the forked version that Ubuntu now provides. If that is the case then you can compile FFmpeg by following [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), use [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or get a simple static binary from the [FFmpeg download](http://ffmpeg.org/download.html) page, but I'm not sure if the PPA or the static binaries support V4L2.

See the [video4linux2 ffmpeg documentation](http://ffmpeg.org/ffmpeg-devices.html#video4linux2) for more info and examples.

---

### Post by squakie on 2012-12-28
Thanks!

---

### Post by squakie on 2013-06-25
Turns out it isn't compatible with linux.

---

