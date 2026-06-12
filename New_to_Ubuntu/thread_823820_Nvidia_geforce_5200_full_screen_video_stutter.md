---
title: "Nvidia geforce 5200 full screen video stutter"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by nakshathram on 2008-06-09
Hi,
  I have a dell inspiron 8600 laptop with nvidia geforce 5200 video card. I installed Adobe flash player to watch google/youtube videos. The video runs smoothly when it is in its regular size, but if I make it full screen, it stutters.

Can someone help me fix this?

I am new to Ubuntu, trying out Ubuntu and XP with dual boot. I am having to login to XP every time I want to watch a video full screen.

thanks in advance!
nakshathram

---

### Post by diablo75 on 2008-06-09
I believe the issue is with Flash, and not your video card.  Performance on video playback that's been made full screen (like when you hit the fullscreen button on a youtube video) is a bit choppy...I've never seen it perform well on my PC, but then again, my PC isn't exactly top shelf.

You could try using Compiz's Enhanced Zoom feature.  You may want to check your keyboard bindings, but I believe the default is Windows-button+Scroll-Wheel up (to zoom in)/down (to zoom out).

But someone else might have a better idea....

---

### Post by EG0R on 2008-07-09
That's not a Flash issue. I've got the same problem with GeForce 5200 causing artifacts in fullscreen video playback. Tried different players, no good. The artifacts look like fast moving black & white horizontal pixel-height lines. They continue moving even when video is on pause, screenshot pictures are artifacts-free.
Tried replacing video adapter (with GeForce4 Ti 4200) without even changing anything in the system - and fullscreen playback works fine!
Any idea or experience on solving this?

P.S.
Using Kubuntu 7.10, 8.04 + DVI video output.
Here's what's in my xorg.conf:
   Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
   EndSection

---

### Post by ellgor on 2008-07-10
Hi,

It sounds more like the nvidia is not configured properly, try this, check to see  if you have a package called nvidia-settings, install if not (synaptic), then, open a terminal and type in "gksudo nvidia-settings" dont use the quotes, a new window will open with the settings for you to play with, adjust accordingly, hope this helps.

Regards, Ellgor.

---

### Post by EG0R on 2008-07-14
ellgor, thanks for the idea! But nvidia-settings is supposed to be used with the NVIDIA X driver. I'm using nv driver. And it works fine with other nvidia videocard I've tried (without changes to configuration).

---

### Post by mrwilloby on 2008-08-21
I have the exact same problem: artifacts in full screen video with an NVIDIA 5200 card.

I don't know what driver I'm using, and I'd rather not go get a different card.

Any advice?

---

### Post by doorknob60 on 2008-08-22
It's a bug with Nvidia and Flash, they don't like each other, so in many cases Hardware Acceleration doesn't work in Flash. I used to have that same card and the same problem. Even with my 8400GS it was slower than it should be. Try [Flash 10]("http://labs.adobe.com/downloads/flashplayer10.html"), it fixes the problem most of the time (I'm pretty sure it did on my 5200, don't actually remember, but I know it helps at least).

---

### Post by mrwilloby on 2008-08-22
I should have been a little more clear. I had the same exact problem as EG0R. There are artifacts with any video, not just Flash video, when played full screen. This includes DVDs and XviD files.

Does this change the situation?

---

