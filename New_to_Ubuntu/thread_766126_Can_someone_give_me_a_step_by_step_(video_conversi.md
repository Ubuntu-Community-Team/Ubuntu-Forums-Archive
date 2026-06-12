---
title: "Can someone give me a step by step (video conversion content)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ericxhall on 2008-04-25
Taking a video from YouTube, and finishing with burning it to a DVD?

---

### Post by subzero316 on 2008-04-25
There are severl online sites that do that try this [www.savevideodownload.com]("www.savevideodownload.com")

There paste the link of the Youtube video. It will download the video to your pc.

Then convert it using the command
$ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.mpg
 where video.flv is the downloaded file and video.mpg is the output file

Then burn it into the dvd

---

