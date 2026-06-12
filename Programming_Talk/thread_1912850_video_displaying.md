---
title: "video displaying"
date: 2012-01-21
forum: Programming Talk
---

### Post by Hetepeperfan on 2012-01-21
Hello everyone,

I want to display a video window (without sound). I've got this camera that provides me with a pointer to an unsigned char buffer. Lets say that i would like my camera to run at 50 Hz and provide me with 640*480*1  frame sizes. Then every pixel from the camera is one byte and represents luminance not color. I must allocate the buffers myself using the C++ new operator. Then I'll tell the camera which buffer to fill with data. So I can choose to have 10 buffers for example. Once I get a frame from the camera, I tell the camera API to fill my next allocated buffer with the next frame.
Now the question for which I can use sow advise is the following. I would like to see my camera frames in a window. Now what library could help me achieve to achieve this? I've been looking at FFMPEG and gstreamer. But gstreamer most strongly suggest not to inject you own data in a pipeline. Now what is the most efficient way to put my data from the camera on the screen.
I'm hope to find some advise here.

Kind regards,

---

### Post by Hetepeperfan on 2012-01-24
Bump and rephrase:

The basic question is how can i get a video on screen, which library should i use?

Like I said before I have got a camera that presents me with grayscale frames.  each frame is for example 640 * 480. That means that each frame fills a unsigned char* = new unsigned char[ 640 * 480 * 1]. I've got 10 of these buffers so I can save 10 frames in memory. I  really would like to know how i  can put these frames to my screen in a window. When the 10 th buffer is filled ( unsinged char** my_frames [9]) the camera fill the first buffer again.
I know I probably need to convert the image to RGB values, but i'm interested in showing these to the users of my program in real time/on the fly.

Has anyone any ideas what is the best tool for this job? Any help is very much appreciated.


kind regards,

Maarten

---

