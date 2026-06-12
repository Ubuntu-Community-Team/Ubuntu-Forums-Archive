---
title: "How to convert video to MKV"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by virus7 on 2013-05-21
hi there I want to know that how can i convert my Mp4 video to MKV video for an example.
I was trying AVIDENUX but am looking for some other options as well. 

thanks

---

### Post by iamkuriouspurpleoranj on 2013-05-21
Arista?

---

### Post by Baldrick_NZ on 2013-05-21
Handbrake. Also now has support for Bluray. 

You'll need to load the PPA too from the link below...

[HTML]http://www.webupd8.org/2013/05/video-transcoder-handbrake-099-released.html[/HTML]

---

### Post by c2tarun on 2013-05-21
[http://stackoverflow.com/questions/8075992/using-ffmpeg-convert-a-file-from-one-format-to-another](http://stackoverflow.com/questions/8075992/using-ffmpeg-convert-a-file-from-one-format-to-another)

I heard that ffmpeg is fastest. Also I never faced an issue in converting avi or flv to mp4. I hope this might help you.

---

### Post by czgirb on 2013-05-21
I have AVIdemux and Handbrake installed
**xxx => AVI** .... go with AVIdemux
xxx => MP4 or MKV ... go with Handbrake
Based on my experienced **Handbrake is the BEST ... it's FAST**

---

### Post by andrew.46 on 2013-05-21
You would simply be swapping containers so there are many applications that will do this. My own personal favourite is mkvtoolnix and this one is always handy to have available...

---

### Post by virus7 on 2013-05-21
Thank you very much all.....

---

### Post by FakeOutdoorsman on 2013-05-21
Current ffmpeg example (not sure if it will work with the libav chaff in the repository):
```
ffmpeg -i input -codec copy -map 0 output.mkv
```
This will copy all input streams (video, audio, subtitles, data, etc) from the input to the output without re-encoding.

---

