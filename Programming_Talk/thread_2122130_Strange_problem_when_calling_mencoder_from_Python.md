---
title: "Strange problem when calling mencoder from Python"
date: 2013-03-04
forum: Programming Talk
---

### Post by guyfromthenorth on 2013-03-04
Hi,

I'm new to this forum. I've found help here a few times in the past to various problems, but this time googling didn't bring me closer to a solution. I've encountered a strange problem when using mencoder to use record video from the webcam through two python scripts.

I've been using the following command to record video without sound:

mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -quiet -nosound -ofps 30 -ovc lavc -lavcopts vcodec=mjpeg -o test.mpeg

This works perfectly on it's own and when called through a simple python script with the following command in Python 2.7.3:

os.system('mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -quiet -nosound -ofps 30 -ovc lavc -lavcopts vcodec=mjpeg -o test.mpeg &')

This gives the following output:

Start rec detectedMEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team


WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Acer Crystal Eye webcam
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
[V] filefmt:9  fourcc:0x32595559  size:640x480  fps:30.000  ftime:=0.0333
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x4eca20]using unscaled yuyv422 -> yuv420p special converter
videocodec: libavcodec (640x480 fourcc=47504a4d [MJPG])
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
v4l2: select timeout
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
End rec detected

Start rec and end rec are simply my own commentaries to detect the right starting and stopping time for the video recording. As mentioned before, this python script works just as I want it to.

When I however call this script through another python script (which handles the user interface) with:

os.popen('./name-of-file.py &')

Now the video does not work. Otherwise the original script seems to do everything it's supposed to do. Now it gives the following output:

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
Forcing audio preload to 0, max pts correction to 0.
v4l2: select timeout
v4l2: ioctl set mute failed: Invalid argument


Running the script this way consistently seems to create a video file 'test.mpeg' which is 9.5KB. It is as if mencoder would be shut down before it has a time to start.

My programming skills are quite limited, and that's the reason why I've separated the two python scripts. In that way it was much easier to make sure that the various parts would work as intended. 

Does anyone know any reason for this strange behavior? Any help would be greatly appreciated!

---

### Post by The Cog on 2013-03-04
I'm making a wild guess here, but:
that '&' on the end of the command puts it into the background, allowing the user to continue typing other commands. I wonder if it is allowing the command (and os.system) to return while mencoded is still running. If the command exits that way, it will kill mencoder in its tracks. So perhaps try without the trailing '&' and see if that works. 

Assuming that's the fix, and you want to exit the script leaving mencoder running, I think adding "& disown" to the end of the command string might do the trick. Note that the subprocess module is the recommended way to do this kind of thing now.

---

### Post by guyfromthenorth on 2013-03-04
Thank you for your answer! I tried your suggestions, but unfortunately it did not seem to fix the problem. Perhaps this is a good reason to read up on subprocesses, it could clean up the code in any case and I will surely learn something in the process.

---

