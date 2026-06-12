---
title: "Simple conversion software code in C"
date: 2012-01-28
forum: Programming Talk
---

### Post by Adam Jensen on 2012-01-28
I'm thinking about creating a conversion tool in C. I don't plan on selling it, it will just be a little hobby project for me (I'll probably make it open source and give it away for free). Where do I begin? Are there any open source conversion apps that I can learn from? I'm interested in converting media files.

---

### Post by lisati on 2012-01-28
*Thread moved to **Programming Talk**.*

---

### Post by cgroza on 2012-01-28
What do you want to convert?

---

### Post by Adam Jensen on 2012-01-28
I would like to convert media video and audio files such as mp3, wma, wmv, mp4 etc.. I would also like to create a DRM removal tool (which will be built into the app). I have a few movies on my computer that I bought in iTunes and would like to burn them to DVD so I can watch them on my TV =P. The few programs that remove DRM and convert media files leave undesirable watermarks and you have to buy a "pro" version to remove them. The conversion tool that I want to create will convert popular formats and remove DRM without adding watermarks, for free =).

---

### Post by Adam Jensen on 2012-01-29
I found the answer I was looking for. Apparently, I need to use the libavcodec library for media file conversions. The library can be found here if anyone is interested:[http://ffmpeg.mplayerhq.hu/download.html](http://ffmpeg.mplayerhq.hu/download.html).

---

