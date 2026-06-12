---
title: "extract motion vector info from video"
date: 2011-01-30
forum: Programming Talk
---

### Post by lavinog on 2011-01-30
I am re-visiting a project I was working on in the past.

The project involves removing security camera footage where nothing occurs (no movement)

In the past I ran a script that decomposes the video frames into images, then compares each frame to determine if there was movement.

This approach worked, but was time consuming.  It seems that the motion information is already decoded into the video stream anyway, why not use that information.  Does anyone have any experience with this?

---

### Post by worksofcraft on 2011-01-30
> **lavinog said:**
> I am re-visiting a project I was working on in the past.

The project involves removing security camera footage where nothing occurs (no movement)

In the past I ran a script that decomposes the video frames into images, then compares each frame to determine if there was movement.

This approach worked, but was time consuming.  It seems that the motion information is already decoded into the video stream anyway, why not use that information.  Does anyone have any experience with this?

My understanding is that the very basis for mpeg encoding is to only encode the changes between successive images... so like a static picture will produce a very small mpeg file.

The biggest problem with security cameras is irrelevant motion such as bushes moving in the wind... or even just their shadows which can be in different places at different times of the day and still sway in the wind, so it's hard to exclude them :(

---

### Post by lavinog on 2011-01-30
> **worksofcraft said:**
> My understanding is that the very basis for mpeg encoding is to only encode the changes between successive images... so like a static picture will produce a very small mpeg file.

This is true except that it is common to use keyframes (whole images) every couple of frames.
In normal video, they can be small enough to ignore, but when dealing with weeks of video, it can consume a large amount.

> 
The biggest problem with security cameras is irrelevant motion such as bushes moving in the wind... or even just their shadows which can be in different places at different times of the day and still sway in the wind, so it's hard to exclude them :(
This can be blocked out by requiring a certain amount of movement, or require a blob of a certain size.

The following command shows what I mean about the motion vectors:
```
ffplay -vismv 1 videofile
```


I have been playing around with using ffmpeg to create the log file from the 1st pass of 2pass encoding.  With that info I can roughly determine when there is activity, but it may not be accurate.

---

