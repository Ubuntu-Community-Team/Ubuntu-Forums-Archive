---
title: "Video and HDMI sound driver Radeon HD 5650"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by sebwes on 2012-04-27
I can't seem to get video and sound drivers working properly. Have tried several times to install the fglrx driver. But driver in use under system details says VESA: PARK.

I haven't found a way to get sound through the HDMI either. 

My computer is a Acer Aspire 5740g with Radeon HD 5650 video card. Running ubuntu 12.04 x64

Where can I find the proper drivers? And how do I install them?

Thanks in advance.

---

### Post by cromat on 2012-04-27
Did you go through the ubuntu install driver application? Ubuntu has already packaged ATI drivers (made by AMD) in their repositories and those ones generally work better than installing directly from AMD on Ubuntu.

The application is called "Additional Drivers"

---

### Post by sebwes on 2012-04-27
yea I used the additional drivers from system settings.

Ok now it says over there that the driver is activated and in use. However it still says that VESA: PARK driver are used when I look at system details. Which info can I trust?

Driver seems to be working better now at least. Now I can use extended desktop instead of only mirrored desktop like before so maybe the problem is solved.

There is an updated additional driver to chose but that one won't install correctly. Do I need it? 

I the sound finally working through HDMI. Only needed to reinstall alsa it seems.

Thanks for help and answers.

---

### Post by cromat on 2012-04-27
For me I run a ATI 5870 and the "post-release" driver always ends badly for me. I have been using the one in the additional drivers without issue. I also have tried the one on the ATI site and have also had issues before. The non-post release one has been heavily tested and from what I can see runs pretty solid. Since Linux isn't a hard core gaming environment, running a driver a few releases old isn't going to matter much, unless there is a specific defect which is causing problems that is fixed.

I'm on my work machine right now, otherwise I would check to see what my system says, however, if you can get sound through HDMI it has to be using the ATI proprietary driver. I didn't think the open source driver supported it yet.

---

### Post by sebwes on 2012-04-27
Ok, thanks for letting me know.

---

