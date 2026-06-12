---
title: "make a single snapshot from /dev/video0 with mplayer ?"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by honeybear on 2012-03-12
Hello, to show the webcam, you can run```
 mplayer tv:// -tv driver=v4l2:device=/dev/video0
``` 
  
I would like to know how to make a single png using mplayer or mencoder, that would be used via crontab (limited sh)? 

thank you

---

### Post by TeoBigusGeekus on 2012-03-12
```
cd /path/to/desired/destination/folder
mplayer tv:// -tv driver=v4l2:device=/dev/video0 -vo png -frames 1
```

---

### Post by honeybear on 2012-03-13
> **TeoBigusGeekus said:**
> ```
cd /path/to/desired/destination/folder
mplayer tv:// -tv driver=v4l2:device=/dev/video0 -vo png -frames 1
```

wow thanks. Now I remember I did that too in the past. 

would you eventually know how to add a delay, because it outputs sthg green or black?

---

### Post by TeoBigusGeekus on 2012-03-13
It shouldn't do that... I don't know...

PS:Try with
```
mplayer tv:// -tv driver=v4l2:device=/dev/video0 -vo png:z=9 -frames 1
```
for compressed png images.

---

### Post by honeybear on 2012-03-13
still green :( :(

I habve tried with z=100 but sztill green :(

```
~$ mplayer tv:// -tv driver=v4l2:device=/dev/video0 -vo png:z=9 -frames 1
MPlayer SVN-r31918 (C) 2000-2010 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Webcam-101
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xa8fbc30] BICUBIC scaler, from yuyv422 to rgb24 using MMX2
VO: [png] 640x480 => 640x480 RGB 24-bit 
png: . - Output directory already exists and is writable.
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   1/  1 ??% ??% ??,?% 0 0 

v4l2: ioctl set mute failed: Invalid argument
v4l2: 3 frames successfully processed, 0 frames dropped.

Exiting... (End of file)

```

maybe mencoder or ffmpeg are better png maker ...?

---

### Post by sloMoses on 2013-01-12
> **honeybear said:**
> still green :( :(

I habve tried with z=100 but sztill green :(

maybe mencoder or ffmpeg are better png maker ...?

I do realize that this thread is almost 11 months old. But I thought I might be able to add some information in case others search later and run across the issue.

I use Slackware, but I found this thread while Googling for exactly what you were trying to do (frame capture from /dev/videoX device using mplayer).

If your device is a webcam (mine is), it usually takes a small amount of time for the webcam to initialize once it realizes that something is trying to access it. That is likely why you get the green screen PNG files. The "z=" flag is an image compression level flag and doesn't affect the green issue you described.

Basically, setting -frames=1 causes mplayer to grab a frame before the camera even realizes that something is trying to access it

The webcams, at least mine, need time to "wake up" and also to analyze the environment with their internal circuitry and perform exposure adjustments, etc. Grabbing the first frame results in the camera not even being "awake" when the frame is grabbed, resulting in the green image that you describe (I get it, too with -frames=1).

A solution, at least what worked in my case, was to change -frames=1 to something like -frames=25. You will get a series of PNG files named something like 00000001.png through 00000025.png.

If you look at the images in sequence (1 through 25) you will see what happens. The first frame (or few frames) will likely be green, before the camera is functional. Then you may see an image that looks familiar but is under/over-exposed, etc. That's when the camera is waking up and figuring out the environment and making internal adjustments to improve the image quality.

On my system/camera, it takes about 7-8 frames for the image to be the best quality.

---

