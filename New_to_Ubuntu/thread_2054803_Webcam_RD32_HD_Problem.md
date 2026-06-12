---
title: "Webcam RD32 HD Problem"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Deguoxiaoma on 2012-09-08
Hi Forum,

I was trying to find an existing post, but did not find anything, if I overlooked something apologize in advance. 

I am on Ubuntu 11.10 / Intel Celeron CPU 2,2 Ghz, 4 Gig RAM, the camera is a Redleaf RD32 II [http://www.hkredleaf.com/product_show.asp?id=1&classid=26](http://www.hkredleaf.com/product_show.asp?id=1&classid=26)

My problem is that I can not get it running via Cheese or anyother programm, I would like to use to create some time elapse. 

I tried around in the terminal and got the following info:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b09c Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 05e1:0b02 Syntek Semiconductor Co., Ltd 
markus@Ubuntu-Markus:~$ lsmod | grep video
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
video                  18908  1 i915

Anyone any idea, what I can do to get it running? 

Thank you very much for your support!

Cheers,

---

### Post by coldraven on 2012-09-08
Have you tried using ffmpeg to extract frames from the AVI file that your camera produces?
You might have to convert the AVI, I have never tried this.
[http://pr0gr4mm3r.com/linux/how-to-create-a-time-lapse-video-using-ffmpeg/](http://pr0gr4mm3r.com/linux/how-to-create-a-time-lapse-video-using-ffmpeg/)

---

### Post by Deguoxiaoma on 2012-09-09
Hi thanks for your answer. I guess that would be the next step. I do not get the camera running in Ubuntu at all :( Any idea, what I could do to get it running and controlled by e.g. Cheese?

thx

---

### Post by coldraven on 2012-09-11
> Any idea, what I could do to get it running and controlled by e.g. Cheese?
I'm no expert but unless it came with a Windows program that can control it I doubt if that is possible. I guess it just shows as a USB mass storage device in Linux.
But someone might know,  good luck.

---

