---
title: "[SOLVED] Raw video stream"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-08
Which program must I use to play raw video stream files?

I got such a file for:

```
luvcview -S -f yuv
```

This command captures raw frames from the webcam and outputs it as a single file stream.raw. How do I play this?

Thanks.

---

### Post by patrickballeux on 2008-10-08
Try with ffplay -f rawvideo -s 320x240 -r 15 YOURFILE

ffplay is part of ffmpeg package.

But you could record (with sound) using gstreamer instead...

Here is my command line to do that from a V4L device...

gst-launch alsasrc ! audiorate ! audio/x-raw-int,rate=44100,channels=2 ! audioconvert ! vorbisenc ! queue ! muxout. v4lsrc device=/dev/video2 ! video/x-raw-rgb,width=320,height=240 ! videorate ! video/x-raw-rgb,framerate=15/1 ! ffmpegcolorspace ! theoraenc quality=63 ! queue ! muxout.   oggmux name=muxout ! filesink location=webcamrecording.ogg


Yours should be like that (v4l2src instead of v4lsrc): 

gst-launch alsasrc ! audiorate ! audio/x-raw-int,rate=44100,channels=2 ! audioconvert ! vorbisenc ! queue ! muxout. v4l2src device=/dev/video0 ! video/x-raw-rgb,width=320,height=240 ! videorate ! video/x-raw-rgb,framerate=15/1 ! ffmpegcolorspace ! theoraenc quality=63 ! queue ! muxout.   oggmux name=muxout ! filesink location=webcamrecording.ogg

Read the gstreamer documentation for setting options for your webcam.
(if **video/x-raw-rgb** does not work, try with **video/x-raw-yuv**)

Good luck!

---

### Post by Eto_Demerzel on 2008-10-08
> Try with ffplay -f rawvideo -s 320x240 -r 15 YOURFILE

This sort of worked, except the video was garbled. Oh, -r is not an option in ffplay, I dropped the -r 15. 

The following worked perfectly (after messing around for some time with the sound recorder, the mic and volume control):

gst-launch alsasrc ! audiorate ! audio/x-raw-int,rate=44100,channels=2 ! audioconvert ! vorbisenc ! queue ! muxout. v4l2src device=/dev/video0 ! **video/x-raw-yuv**,width=320,height=240 ! videorate ! **video/x-raw-yuv**,framerate=15/1 ! ffmpegcolorspace ! theoraenc quality=63 ! queue ! muxout. oggmux name=muxout ! filesink location=webcamrecording.ogg

Thanks a billion, Patrick! =D> You're the man!!

I was determined to get it working using ffmpeg:

```
ffmpeg -f audio_device -i /dev/audio -s 640x480 -f video4linux2 -i /dev/video0 test.mpeg
```

This works too.

---

### Post by patrickballeux on 2008-10-08
Ah, yes, for ffmpeg there is the video4linux format, I had forgot about it.  

But I find gstreamer more flexible as you can add filter to it.  But ffmpeg can output directly to the desired format.

The only glitch that I got with FFMPEG was that sometimes, the video and sound is out of sync for long recording.

For more fun, you can use Jack for your sound recording (with gstreamer): see [http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack]("http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack")


Have fun!

---

### Post by Eto_Demerzel on 2008-10-08
Thanks! :)

---

