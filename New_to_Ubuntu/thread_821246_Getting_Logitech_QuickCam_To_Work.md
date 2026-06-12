---
title: "Getting Logitech QuickCam To Work"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-07
Hi, 

Most of the time, I've been lucky to simply plug a gadget into my computer, and it just works. I just got a Logitech Quickcam and unfortunately this is not the case (I don't think). 

I run v7.10 for a 64-bit PC. 

Can anyone help me out with where to start?

I'm not particularly computer savvy, so please don't be afraid to rrrreally dumb it down for me. 

Thanks so much! :)

---

### Post by rburkartjo on 2008-06-07
ok, first i had to upgrade to ubuntu 8.04 and then install cheese. go to applications/add/remove/the type in cheese in search/ then install cheese.
see what happens. cheese is installed under application/graphics./cheesemaker

---

### Post by OKnotOK on 2008-06-07
I have installed it, but it just shows a multi-color screen when I try to record with it. (You know, like the kind of screen that shows up when you fall asleep in front of the tv, and wake up to find the channel is off-air)

---

### Post by OKnotOK on 2008-06-07
Anybody have any ideas about this? Or can anyone name a different program that I could use?

---

### Post by OKnotOK on 2008-06-07
Okay for some reason, on the third or fourth time that I started Cheese up, the camera started working... Ubuntu's magic has come through for me once again!!!

---

### Post by OKnotOK on 2008-06-07
I have the camera working, but there's no sound.

I've tried making a test recording using 

applications > video & sound > sound recorder

but I'm not able to record anything. 

So is this a headset problem? Or could there be something else at work here?

(Incidentally, I can HEAR through the headset -- but the mic is not working??)

---

### Post by OKnotOK on 2008-06-07
*Bump*

Boy this forum moves fast!

Can anyone help with my post above?

---

### Post by halln on 2008-06-07
try if your webcam's working with ekiga, I think you can check it from there if your webcam and mic is working properly.

---

### Post by OKnotOK on 2008-06-07
Is ekiga like skype? A phone-calling device?

Because my microphone doesn't work with skype either. 

Its the mike that's not working. The camera is fine.

---

### Post by TeoBigusGeekus on 2008-06-07
Type
```
alsamixer
```
and go to the mic column. See if the mic input is muted or very low.

---

### Post by TeoBigusGeekus on 2008-06-07
When you've typed alsamixer, press the right button on your keyboard (->) and move to the mic column. There, press the up button (^) to increase the mic sensitivity.

---

