---
title: "Video issue with connecting HDMI to TV"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by gabriel23 on 2014-06-12
When I connect my frontend/backend PC to my TV through the HDMI cable, you see the following picture.

[http://imageshack.com/a/img820/1638/pu3o.jpg](http://imageshack.com/a/img820/1638/pu3o.jpg)

Essentially, the bottom of the screen is blank and content near the middle of the screen is truncated. When I try changing the display, my option of keeping the 1980x1080 for the TV disappears and the highest resolution available is 1280x720. So while I'm running my monitor and TV at the same time, everything looks great on my monitor but the TV picture cuts a lot of the screen out.

I haven't even tackled the lack of audio through the HDMI cable (most likely I'll just use optical for audio).

I'm using the AMD Athlon 5350 for my video.

---

### Post by rahul4557 on 2014-06-12
-Check if your TV is FULL HD ie it supports 1080p.
-Check the HDMI cable.
-Check if proprietary drivers are installed for Display Driver.(If not install)
-Check in Control Center for AMD if display frequency is correctly set.(If Proprietary Drivers are installed for Radeon).

Good Luck

---

### Post by gabriel23 on 2014-06-12
I had the open source drivers installed. Once I changed it to the proprietary drivers it worked. Thanks!

---

