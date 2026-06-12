---
title: "sound problems after upgrade to Ubuntu 8.04"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by aam-aadmi on 2008-05-01
I am using Ubuntu on a HP dv2500t. I upgraded from Ubuntu 7.10 to Ubuntu 8.04 yesterday. While the sound was working perfectly with 7.10, now (with Ubuntu 8.04) the sound is totally screwed up! I can hardly hear anything and the quality is also very bad.

Any ideas on how to get around this problem?

---

### Post by kshtjsnghl on 2008-05-01
hey see if you have selected the correct device in the volume controls>file>device.

Besides try checking all the options in the preferences and try changing the volume in all the switches.

or see that you have installed all the plugins and that your hardware has been recognised properly .

For that you can go the restricted hardware and hardware testing the system>administration option.

---

### Post by aam-aadmi on 2008-05-01
Thanks for the advice. Just opening up the volume control and tinkering with the switches a bit solved the problem!

---

### Post by cnewswanger on 2008-05-01
I have a M-Audio Delta 1010lt card based on the ICE1712 device.
Envy24 worked great under 7.10.

I upgraded and now modprobe does not see the driver.

Apparently the driver is not enabled in the kernel for 8.04.

Does anyone know IF this might be fixed?

This is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974)

---

