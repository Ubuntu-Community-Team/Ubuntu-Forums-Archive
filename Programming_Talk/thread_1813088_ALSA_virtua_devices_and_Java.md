---
title: "ALSA virtua devices and Java"
date: 2011-07-27
forum: Programming Talk
---

### Post by minerbog on 2011-07-27
Hi All,

Right, Ill try and explain this the best I can.

I have create via .asoundrc a "virtual device" in ALSA. This basically splits my 7.1 ESI Gigaport USB device into 4 stereo outputs named StereoOut1 thru 4 (I know, not very original!!). In Audacity, these show up perfectly and can be used as expected.

When I list the available sound devices in Java using the javax.sound api, all I get is the devices (ie cards) themselves. Now I'm assuming that it is because the Java sound API can only pick up the main "mixers" link to the physical device? Correct me if I'm wrong please!

So, the question is, can I create a dummy physical device that java can find and use that links to the ALSA virtual devices I have created?

Many Thanks

Gavin.

---

