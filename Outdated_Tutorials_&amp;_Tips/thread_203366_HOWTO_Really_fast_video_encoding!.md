---
title: "HOWTO: Really fast video encoding!"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by weijie90 on 2006-06-25
Hi all,

most users use burn 360 to encode videos to the VCD format. Sadly, the cute GUI that ffmpeg uses is much slower then the command line. 

The solution:

Run burn 360 and start encoding your file.

Open the terminal, and enter:
```
ps aux | grep ffmpeg
```

Nice! now you see the full command that burn 360 uses to encode your file. 
```
ffmpeg -i <input> <options> <output>
```

Close burn 360 and run this command in the command line.

Thats much faster- but how long will it take? 

Search the ffmpeg outout for something like this:

```
Input #0, avi, from '/home/di/Desktop/video.avi':
  Duration: 01:49:29.7, start: 0.000000, bitrate: 867 kb/s
  Stream #0.0: Video: msmpeg4, 720x480, 23.98 fps
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 112 kb/s

```

multiply the no. of secs in "duration" with the fps. simple math.

look at the last line-
```
frame=146863 q=0.0 Lsize=  997168kB time=5874.5 bitrate=1390.6kbits/s

```

and get a % value. sweet CLI magic!

---

