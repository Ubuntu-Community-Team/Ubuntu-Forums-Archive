---
title: "Fast video playback with ffmpeg and x264"
date: 2010-12-11
forum: Programming Talk
---

### Post by sabatier on 2010-12-11
Hi

I'm running the opencv samples and the video playback is about twice the speed it should be. I'm guessing it's something to do with my installation of ffmpeg/x264. I followed the installation tutorial here: [http://ubuntuforums.org/showthread.php?t=786095&highlight=x264](http://ubuntuforums.org/showthread.php?t=786095&highlight=x264)

Anyone got any ideas what's wrong?

---

### Post by FakeOutdoorsman on 2010-12-11
Does it also playback at the incorrect speed if you use ffplay?
```
ffplay input.foo
```

---

### Post by sabatier on 2010-12-12
> **FakeOutdoorsman said:**
> Does it also playback at the incorrect speed if you use ffplay?
```
ffplay input.foo
```

No actually, it plays just fine. I guess it's not ffmpeg then?

---

### Post by sabatier on 2010-12-12
OK it appears as if OpenCV is setting the wrong frame rate. When I do this command, the video plays fast again:

ffmpeg -i input.mkv -f yuv4mpegpipe - | yuvfps -s 50:1 -r 50:1  | ffmpeg -f yuv4mpegpipe -i - -b 28800k -y output.mkv

Now why is OpenCV doing this?

---

### Post by FakeOutdoorsman on 2010-12-12
Your input is being decoded by FFmpeg and piped to yuvfps into a format it can read. Then yuvfps interprets the input as 50 fps (even if it is actually 24 fps, for example) and specifies the output as 50 fps. Finally, it is piped to FFmpeg to be re-encoded.

See **man yuvfps** for more info on that command.

I don't know why OpenCV is doing this unless someone wanted to double the speed of a 24 fps input and required an output file with 50 fps.

---

