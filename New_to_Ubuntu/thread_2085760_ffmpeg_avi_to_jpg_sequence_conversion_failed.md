---
title: "ffmpeg avi to jpg sequence conversion failed"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by twocorners on 2012-11-18
hello, i'm trying to make a jpg sequence from an avi clip. i've done it before, but with this video it's not working for one reason or another. instead it says "operation not permitted", "no such file or directory" or something else. i've been trying different ways of specifying the directory and such. this is the command that worked the first time.

ffmpeg -i /home/homeskillet/Downloads/Windofchange.flv image%03d.jpg 

i put the directory and the video name there to show what worked. i used the same command, changing the video name of course. it's in the same directory, yet this and every other thing i tried came up with nothing. any help would be appreciated.  :)

---

### Post by squakie on 2012-11-18
I could be WAY off base here, because I've done very little with images, but I thought the output you are looking for needed to be GIF, not JPG.  At least, that's what we used to use for animations a long, long time ago on websites.

---

### Post by FakeOutdoorsman on 2012-11-19
Please show your non-working ffmpeg command and the resulting complete console output.

---

### Post by twocorners on 2012-11-19
thanks for replying so quickly.

fakeoutdoors, here are the commands i tried. i kept thinking maybe there was a typo or a wrong directory (forgive any misused terminology ^.^').

 ffmpeg -i /home/Home/Downloads/first frame project first edit.avi image%03d.jpg

ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
/home/Home/Downloads/first: No such file or directory

  ffmpeg -i /home/Home/Downloads/ firstframeprojectfirstedit.avi image%03d.jpg

ffmpeg -i /home/homeskillet/Downloads/firstframeprojectfirstedit.avi image%02d.jpg

<<(as i'm doing these commands over, this command created the image  sequence (yay!) but there's something seriously wrong with the quality)

ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, avi, from '/home/homeskillet/Downloads/firstframeprojectfirstedit.avi':
  Metadata:
    encoder         : Lavf53.21.0
  Duration: 00:00:03.67, start: 0.000000, bitrate: 5539 kb/s
    Stream #0.0: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 8:9 DAR 4:3], 104857 kb/s, 29.97 fps, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 128 kb/s
Incompatible pixel format 'yuv420p' for codec 'mjpeg', auto-selecting format 'yuvj420p'
[buffer @ 0xa05d3a0] w:720 h:480 pixfmt:yuv420p
[avsink @ 0xa05dc20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0xa0e93a0] w:720 h:480 fmt:yuv420p -> w:720 h:480 fmt:yuvj420p flags:0x4
Output #0, image2, to 'image%02d.jpg':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: mjpeg, yuvj420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
frame=  110 fps= 87 q=24.8 Lsize=      -0kB time=3.67 bitrate=  -0.0kbits/s    
video:1707kB audio:0kB global headers:0kB muxing overhead -100.001259%


 ffmpeg -i home/homeskillet/ "firstframeprojectfirstedit.avi" "image%04.jpeg

>


ffmpeg -f image2 -i image%03d.jpg firstframeprojectfirstedit.avi

ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
image%03d.jpg: No such file or directory

ffmpeg -f image2 -i /homeskillet/ image%03d.jpg firstframeprojectfirstedit.avi

 image%03d.jpg: No such file or directory


here's the actual command.

ffmpeg -i video.mpg image%d.jpg

although the 3nd one did work now. -_- so i guess that's fixed. is there any way to improve the quality of the images? if not i can work with it. ;)

---

### Post by twocorners on 2012-11-19
squaky, i need an jpg sequence so i can work with every frame separately. :)

---

### Post by dannyboy79 on 2012-11-19
you're getting "/home/Home/Downloads/first: No such file or directory" because you can't have spaces in your filename. You need to use a backslash for spaces. So your command would be the following
```
ffmpeg -i /home/Home/Downloads/first\ frame\ project\ first\ edit.avi image%03d.jpg
```

---

### Post by squakie on 2012-11-19
> **twocorners said:**
> squaky, i need an jpg sequence so i can work with every frame separately. :)

Ah, probably much easier the way you are trying.  I was thinking of making it a gif and then using gimp so you could save each image that way.  If you can get what you are doing to work to your satisfaction, it is MUCH easier than what I was thinking.  ;)

---

### Post by twocorners on 2012-11-20
> **squakie said:**
> Ah, probably much easier the way you are trying.  I was thinking of making it a gif and then using gimp so you could save each image that way.  If you can get what you are doing to work to your satisfaction, it is MUCH easier than what I was thinking.  ;)

yeah, it's up and working now. the result is a sequence of numbered frames all made at once. i agree it's much easier lol. 

dannyboy,thanks for the tip. everything's fixed now.

and thanks to everyone for the comments! i love this forum! :smile:

---

### Post by dannyboy79 on 2012-11-20
> **twocorners said:**
> yeah, it's up and working now. the result is a sequence of numbered frames all made at once. i agree it's much easier lol. 

dannyboy,thanks for the tip. everything's fixed now.

and thanks to everyone for the comments! i love this forum! :smile:
well, what was your solution so in case others come to have the same problem they know how to solve it.

---

