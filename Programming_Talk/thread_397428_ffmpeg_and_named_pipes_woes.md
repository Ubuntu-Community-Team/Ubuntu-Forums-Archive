---
title: "ffmpeg and named pipes woes"
date: 2007-03-30
forum: Programming Talk
---

### Post by crzdude on 2007-03-30
Hi,

I have to add video recording capabilities to a
program that holds /dev/video0 while the record is
being taken. The program has to hold the device for
several reasons and vloopback is not an option for me
since the program is also expected to send commands to
the camera. Therefore, I believe the best solution in
my case is to use a named pipe to feed ffmpeg with my
video data. I am hoping that I will be able to simply
write a copy of my yuv420p data into the named pipe
while ffmpeg grabs data from /dev/dsp on its own. Does
that sound like a good way to solve my problem?

Well... I have been playing with ffmpeg and named
pipes in the command line without success. I have
tried several different versions, codecs, and
combinations of command line parameters to no avail.
This is what I get with the latest SVN snapshot:

This works just fine:

ffmpeg -f audio_device -i /dev/dsp -f video4linux -s
320x240 -i /dev/video0 /tmp/out1.mpg

However this doesn't:

ffmpeg -f audio_device -i /dev/dsp -f rawvideo -s
320x240 -i ./video_fifo /tmp/out2.mpg

... where ./video_fifo is my named pipe and I cat
/dev/video0 into it using another shell. The command
above produces a out2.mpg video but it looks and
sounds like a "fast-forwarded" out1.mpg (i.e., the
video frames are displayed really fast in the screen
and you can barely make sense of the sound). I suspect
that '-f rawvideo' might be contributing to the
problem but I couldn't get ffmpeg to accept an input
from my named pipe w/o specifying this format. 

What am I doing wrong? Any help would be greatly
appreciated.

Best Regards

---

