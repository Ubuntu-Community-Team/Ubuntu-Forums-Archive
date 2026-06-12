---
title: "Monitor Resolution solved - but is there a better way?"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by eeq on 2012-03-24
I have Ubuntu 11.10 installed on an HP Pavilion a1310n with ATI RADEON XPRESS 200 Series video on the motherboard.  When I first installed Ubuntu the screen resolution was 1024 x 768.  I hunted the forums and found the xrandr commands to change the screen resolution to 1680 x 1050 BUT the forums gave instructions for earlier versions of Ubuntu.

I could not find any of the files they suggested I modify.  I finally put the xrandr commands into /etc/profile.  This works but is there a better place to put the instructions under Ubuntu 11.10?

TIA.  Apologies for being so wordy.

---

### Post by Mark Phelps on 2012-03-24
Probably not ... as AMD dropped restricted driver support for that Radeon version years ago.

The default Radeon open-source drivers you have installed now are the only ones that will work, and they do not have the extensive set of features or resolutions that the previous restricted drivers provided.

---

### Post by eeq on 2012-03-25
OK, Thanks.  I will close this post (if I can figure out how!)

---

