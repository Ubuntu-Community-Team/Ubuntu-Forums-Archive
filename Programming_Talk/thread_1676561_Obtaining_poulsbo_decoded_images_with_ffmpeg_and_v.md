---
title: "Obtaining poulsbo decoded images with ffmpeg and vaapi"
date: 2011-01-27
forum: Programming Talk
---

### Post by trease on 2011-01-27
Hi, I'm trying to decode an H264 (1280x720) stream through 
hardware driver using ffmpeg together with vaapi.
I would like to know if I will be able to use decoded
frames not to display them on the screen, but to process
them further on. Substantially for each frame I would 
need to obtain a buffer containing the decoded image.
Can I do this?
I'm encountering some problem during the decode phase and
before going on I need to know if my purpose is possible 
to reach.

I'm using a fitPC2 with Karmic version of Ubuntu
and iegd_drv_video driver installed.

---

