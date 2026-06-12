---
title: "Webcam"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by dwally89 on 2008-04-23
Hi,

I just plugged in my webcam today (for the first time), and it worked straight away with aMSN, however it doesn't work on camorama or easycam2.

Anyone know the reason why?

Thanks

---

### Post by Antman on 2008-04-23
> **dwally89 said:**
> Hi,

I just plugged in my webcam today (for the first time), and it worked straight away with aMSN, however it doesn't work on camorama or easycam2.

Anyone know the reason why?

Thanks

In order to view any errors that camorama is throwing, try opening a terminal window and typing:
```
camorama
```
Then copy and paste the code here.

---

### Post by dwally89 on 2008-04-23
Nothing comes up in the terminal when I type that, however a message box appears saying:
> Error (camorama)
Could not connect to video device (/dev/video0).
Please check connection.

---

### Post by MorningWood on 2008-04-23
I seem to be having the exact same problem except mine is an HP built in cam. Any help would be great.

---

### Post by linuxwizard on 2008-04-23
Camorama does not support v4l2. The Ubuntu forums are full of users asking what the "could not connect to video device (dev/video0)" error message means when they try to use Camorama. One reason is they're using a driver that requires v4l2.

---

### Post by MorningWood on 2008-04-23
> **linuxwizard said:**
> Camorama does not support v4l2. The Ubuntu forums are full of users asking what the "could not connect to video device (dev/video0)" error message means when they try to use Camorama. One reason is they're using a driver that requires v4l2.

So what would our best bet be in terms of fixing this?

I get the following error:

video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [16 bit YUV 4:2:2 (packed, YUYV)]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
ioctl: VIDIOC_REQBUFS(count=1;type=VIDEO_CAPTURE;memory=MMAP): Device or resource busy
capturing image failed

---

### Post by MorningWood on 2008-04-25
Just in case anyone is having the same problems as I was, I figured out what v4l (video4linux, who would have thought?) was and found a great program called **Cheese** that works with V4l2. However; for some reason it doesn't like recording video.

---

