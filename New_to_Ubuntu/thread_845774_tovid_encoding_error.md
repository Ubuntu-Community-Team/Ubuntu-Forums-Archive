---
title: "tovid encoding error"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by KevNice on 2008-06-30
When trying to make a DVD, the first 6 .avi files went fine, until I got to the 7th one... and it stopped with following code (taken from tovid.log):


```
[tovid]: Audio encoding finished successfully.
[tovid]:
[tovid]: =========================================================
[tovid]:
[tovid]: Encoding video stream with the following commands:
[tovid]: nice
-n 0
mplayer -benchmark
-nosound -noframedrop
-noautosub -vo
yuv4mpeg:file="/home/kevin/episode_1:_Babyface.0/video.yuv" -vf
scale=720:576 "/storage/Videos/rescue
me/Rescue Me
- Season
4/Rescue Me
S04E01 (Babyface).avi"
[tovid]: cat
"/home/kevin/episode_1:_Babyface.0/video.yuv" |
yuvfps -r
25:1 -v
0 |
nice -n
0 mpeg2enc
--sequence-length 4300
--nonvideo-bitrate 271
--multi-thread 2
--aspect 2
-f 8
-b 4500
-g 4
-G 9
-D 10
-K hi-res
--frame-rate 3
-v 0
--video-norm p
--reduction-4x4 2
--reduction-2x2 1
-q 8
-o "/home/kevin/episode_1:_Babyface.0/video.m2v"
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.
Playing /storage/Videos/rescue me/Rescue Me - Season 4/Rescue Me S04E01 (Babyface).avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  970.7 kbps (118.5 kbyte/s)
Clip info:
 Software: transcode-1.0.2
Could not parse arguments at the position indicated below:
file=/home/kevin/episode_1:_Babyface.0/video.yuv
                           ^
Unknown subdevice: file=/home/kevin/episode_1:_Babyface.0/video.yuvError opening/initializing the selected video_out (-vo) device.
BENCHMARKs: VC:   0.000s VO:   0.000s A:   0.000s Sys:-938.388s = -938.388s
Exiting... (End of file)
[tovid]: Encode stopped, killing all sub processes
[tovid]: Keeping temporary files used during encoding in /home/kevin/episode_1:_Babyface.0
[tovid]: tovid encountered an error during encoding:
[tovid]:     Couldn't create file: "/home/kevin/episode_1:_Babyface.0/video.m2v"
```


Any ideas? I know that I can use DeVeDe, and I have, it works fine, but I like the menu options with tovid and wanted to make something cool, with music, etc.

---

### Post by halitech on 2008-08-06
not sure whats going on with tovid but have you tried ManDVD? Not in the repos but you can get it from [http://getdeb.net/app/ManDVD](http://getdeb.net/app/ManDVD)

I use it for all my work on putting multiple videos on a single dvd

---

