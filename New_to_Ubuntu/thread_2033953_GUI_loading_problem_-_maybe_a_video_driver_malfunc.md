---
title: "GUI loading problem - maybe a video driver malfunction?"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by berniemacx on 2012-07-27
When I start my computer up the GUI doesn't load and I'm left with a command prompt to login. This problem occured after I installed a proprietary driver for a Radeon HD 4650 from AMD's website. I was also trying to get bitcoin working but having connection problems.
 
I tried deleting the xorg.conf file but the GUI still didn't load. There's an xorg.conf.failsafe file as well as an xorg.conf.fglrx-0 file in my X11 folder. Could that be the problem?
 
I'm a bit of a newbie at all of this. Any explanation about why the commands work the way they do in addition to the instruction to fix the problem would be a real help. Thanks!

---

### Post by levlaz on 2012-08-01
Login and then type 

```
 startx 
``` 

what happens?

---

### Post by Shadius on 2012-08-01
You said you downloaded the graphics card driver from the AMD website. Any reason why you went this route instead of using the *Additional Drivers* that Ubuntu provides? You could try that and see what happens.

---

### Post by anewguy on 2012-08-02
You may also need to add the nomodeset option to the boot line.  I had to do that with my old PC that an integrated AMD6400 series GPU.

---

### Post by berniemacx on 2012-08-02
> **levlaz said:**
> Login and then type 

```
 startx 
``` 

what happens?
A whole lot of script would run before I had a chance to see it but it would just stall after a while.

---

### Post by berniemacx on 2012-08-02
> **Shadius said:**
> You said you downloaded the graphics card driver from the AMD website. Any reason why you went this route instead of using the *Additional Drivers* that Ubuntu provides? You could try that and see what happens.
The fglrx driver in the additional drivers was causing a lot of tearing on the screen. I wanted the 3D rendering but the open source drivers didn't have that. So I thought the latest legacy driver from AMD would be a better option.

---

### Post by ranger1021994 on 2012-08-02
If there is a problem with fglrx then you can watch this
[http://askubuntu.com/questions/98827/ati-driver-re-install-fail]("http://askubuntu.com/questions/98827/ati-driver-re-install-fail")

OR this 
[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts]("http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts")

---

