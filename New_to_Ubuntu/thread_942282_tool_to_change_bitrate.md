---
title: "tool to change bitrate"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by rkakkar on 2008-10-09
i want to change the bitrate of an mp3 file. any tool for that?

---

### Post by hashimoto on 2008-10-09
Install sound converter:
[http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html](http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html)

In the optioins you can select the output format as well as quality.

Remeber that you can only go to lower quality. It does not help to increase the bitrate; the soudn quality will not improve.

---

### Post by unutbu on 2008-10-09
```
sudo apt-get install ffmpeg
ffmpeg -i input.mp3 -b 64k output.mp3
```
This sets the bitrate of the output file to 64kbit/s.

---

