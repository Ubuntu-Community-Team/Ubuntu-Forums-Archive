---
title: "How to get nvidia 3D driver under ubuntu 8.10"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-09
After upgrading to 8.10 from 8.04.1 I found I no longer had any video effects (and lost 80% of the screensavers)

After some research I found the Ubuntu developers changed the video driver API to require new video drivers out of the nvidia company, and the nvidia company choose not to provide support for my "older" legacy cards  (I have a GeForce-4 MX-440 and a GeForce-4 Ti4600).  These were brand new about 4 years ago.

So... after trying many things I decided to check the cost of a new video card.  A new GeForce 6200 with 256 meg of DDR memory was only $49, since I could afford that, I drove to the store and bought one.

So what was needed to get it installed? 

1. turn of computer and remove power cord (off does not always really mean off)
2. replace old video card with new video card
3. replace power cord and power up
4. once logged in and connected to the internet click on "System-Administration-Hardware Drivers"  (this starts a search for available restricted drivers that support the detected video card)
5. select the latest nvidia driver shown (177) and click activate.
6. wait a few minutes while it downloads and installs
7. reboot to start using the new video driver
8. check if the new driver is being used with "System-Administration-NVIDIA X Server Settings", which won't work unless a 3rd party nvidia video driver is running.

So I am happy once again.  But what about all the people in the world who can not afford to just spend $50 when the operating system bumps up a minor revision? (from 8.04 to 8.10).

It seems to me like the ubuntu 8.10 revision should have gone out of it's way to support the earlier video drivers.

Hope this helps clear up some confusion and calms some H/W upgrade fears.

---

