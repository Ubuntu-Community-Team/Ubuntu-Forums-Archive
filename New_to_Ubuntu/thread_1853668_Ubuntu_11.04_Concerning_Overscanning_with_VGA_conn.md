---
title: "Ubuntu 11.04: Concerning Overscanning with VGA connection"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Chemical_Ire on 2011-10-02
Hello there!

I'm having a bit of trouble with ubuntu 11.04 and my 19" Sharp HDTV overscanning the desktop.  I recently had 10.10 installed on another machine and I don't remember having this problem with the same monitor. 

I have done some research into the problem and it seems to be common.  The problem is, everyone else seems to have the problem with HDMI or DVI.  

My video card is an Nvidia 8800gts and the drivers are up to date, and I am connected to the monitor via VGA through a DVI adapter.  I've messed with all sorts of settings in the nvidia server settings and on my monitor but have had no luck.

I am tryign to achieve my monitors 1360x768 setting.

Help please!

---

### Post by mcduck on 2011-10-03
VGA, DVI or HDMI doesn't contain overscan, so if you get any that's purely because of the settings used on your HDTV. Check the TV's settings and enable the pixel-per-pixel mode. (what it's actually called depends on your TV manufacturer and model, but basically it's just a mode that disables all image scaling made by the TV, instead displaying the image *exactly* as it is. This far every single HDTV I've seen has a mode like this so if you can't find anything check the manual.)

---

