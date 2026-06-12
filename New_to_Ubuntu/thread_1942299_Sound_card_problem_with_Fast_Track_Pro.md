---
title: "Sound card problem with Fast Track Pro"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by bitcrow on 2012-03-17
I haven't found any assistant/understandable help so here's my problem:

I cannot use M-Audio Fast Track Pro for my recordings. Sometimes it acts randomly in both Audacity and Ardour. (Sometimes volumes are high, noise appears etc.) So I assume FTP just needs some kind of Linux sound card driver. However M-Audio does not have one in their website. ALSA recognizes FTP though. 

I don't need any advanced solution beyond mono and stereo. I just want to get my recordings work even somehow. Is there any solutions?

I'm using:

[LIST]
[*]Acer AspireOne D255E (yeah, it's a mini-laptop and may not to be best for recordings, but I'm still looking for the simplest, the best or simply the best solution for my problem.)
[*]Ubuntu 10.04 (first it was netbook remix, then I made some Ubuntu studio extensions and I'm not sure now what is it technically and should I get a newer Ubuntu to solve my problem.)
[/LIST]
Changes in sample rate, buffers and so on doesn't change anything. Even Windows 7 (where the driver is installed) creates some random clicks once in a while (which Ubuntu and FTP don't). So I'm pretty out of ideas.

---

### Post by tripolitan on 2012-04-09
Unfortunately, FTPro is output only - no input under ubuntu or any other common distro.The noise is basically electronic noise Coming from your netbook, through your usb and straight to your F T P

---

### Post by bitcrow on 2012-04-10
I've heard that FTP would work after kernel 3.1. For example: [http://yomix.org/info/blog/2011/07/14/m-audio-fast-track-pro-special-features-now-enabled-linux/#comment_55](http://yomix.org/info/blog/2011/07/14/m-audio-fast-track-pro-special-features-now-enabled-linux/#comment_55) 

So, now I'm waiting to update Ubuntu to the 12.04 and maybe with Studio version. But I don't know will it solve my problems.

---

### Post by psychok7 on 2012-04-26
hi there, i just did a fresh install of ubuntu 12.04 and noticed my m-audio fasttrack pro stopped working..

installed pavucontrol , disabled all sound cards and only enabled m-audio (duplex channel) and it started working

after a few minutes it stopped again,  it was working but then after a while the card "disconected".. neither pavucontrol or ubuntu default sound software are recognizing m-audio

---

