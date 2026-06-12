---
title: "Touchpad stopped working making a Lubuntu paperweight of my laptop"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by bozzchem on 2014-04-15
After installing Lubuntu 13.10 on my HP Pavillion dv6700, it worked great for a couple of hours.

Now, the touchpad doesn't work.  I purchased a USB optical mouse to see if that would work and it didn't.

I've searched for remedies online but none are written to the level of a complete beginner.

I did a reinstall of Lubuntu and found the same issue happened again.  After a short while, the touchpad stops working and there is nothing I can do with the laptop.

Any help would be appreciated.  I don't have tons of time for troubleshooting but do want to stick this out rather than reinstalling windows.

---

### Post by jones quest on 2014-04-16
Hi,

HP laptops have an option to disable/enable touchpad. On some laptop models this is done by double tapping on the top left-hand corner of the touchpad area, which can easily happen by accident. There is an old bug ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/576062](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/576062)) where after disabling the touchpad on HP dv6700 it newer wakes up again, and also interfered with keyboard and external mouse. I'm wondering if you are experiencing the same issue. In which case the bug should probably be reopened.

Can you type on the keyboard?

If you can, open up the terminal: either press CTRL+ALT+T or press ALT+F2 and type lxterminal.

Try turning the touchpad off and on with the synaptic driver manager:
synclient TouchpadOff=1 (to turn off touchpad)
synclient TouchpadOff=0 (to turn on the touchpad)

---

