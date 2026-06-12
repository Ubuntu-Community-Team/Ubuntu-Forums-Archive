---
title: "I need a Video Splitter"
date: 2012-04-03
forum: Philippine Team
---

### Post by SHENGTON on 2012-04-03
[SIZE=2]Hello guys, good morning.

Just wanna ask something about splitting the video. Is there a video splitter for GNU/Linux?[/SIZE] [SIZE=2]

Hope someone could help me. Thanks!	[/SIZE]

---

### Post by Script Warlock on 2012-04-04
is that software or hardware..

---

### Post by zeljkojagust on 2012-04-04
Check this thread: [http://ubuntuforums.org/showthread.php?t=890781](http://ubuntuforums.org/showthread.php?t=890781)

---

### Post by tech-hero on 2012-04-04
> **SHENGTON said:**
> [SIZE=2]Hello guys, good morning.

Just wanna ask something about splitting the video. Is there a video splitter for GNU/Linux?[/SIZE] [SIZE=2]

Hope someone could help me. Thanks!	[/SIZE]

You may try the default Video Editor in UBUNTU. :)

---

### Post by Jose Catre-Vandis on 2012-04-04
Using ffmpeg (for a 1 hour long video to be split into two equal parts):
```
ffmpeg -i input.avi -t 1800 -acodec copy -vcodec copy output1.avi
```
```
ffmpeg -i input.avi -ss 00:30:00 -acodec copy -vcodec copy output2.avi
```

if you want to copy out from some where in the middle, just combine -ss and -t (for example 30 minutes clip starting 15 minutes in):
```
ffmpeg -i input.avi -ss 00:15:00 -t 1800 -acodec copy -vcodec copy -output3.avi
```

You may have to use the mkv toolkit for mkv containers

---

