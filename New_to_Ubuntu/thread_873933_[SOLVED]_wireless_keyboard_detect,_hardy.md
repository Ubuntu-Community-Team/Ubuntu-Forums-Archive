---
title: "[SOLVED] wireless keyboard detect, hardy"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by satipera on 2008-07-29
I am trying to use a samsung sdr 4000, the system detects a keyboard as ubuntu boots, but the keyboard does not work with ubuntu, any ideas please?

---

### Post by phidia on 2008-07-29
Most wireless keyboard will work in linux as long as they are detected-and you're saying yours is. You could examine or post the output of > lsusb&> dmesg for more information. Have you tried the easy stuff like resetting the keyboard (usually a little button on the bottom of the keyboard) and checking the batteries?

---

### Post by satipera on 2008-07-29
but I can only do this with the old keyboard connected will this be of any help?

---

### Post by madrunner on 2008-07-29
i have this same problem, my keyboard is dected when i put the Live CD in the choose the options but after taht nothin, im also having this problem with my mouse!
btw its obvouse his batterys work he's using the keyboard now aint he?

---

### Post by phidia on 2008-07-29
> **satipera said:**
> but I can only do this with the old keyboard connected will this be of any help?
 My bad-sorry-no using a wired keyboard won't do much for the wireless problem. There might/should be some info in /var/log/messages though.
What version of ubuntu are you both using? You might try an earlier release and see if it works in that.


When I think about it now. If you have a wired usb keyboard & mouse you could plug those in after the system boots and your wireless doesn't work-like wait a few minutes and then plug in the keyboard/mouse and run those commands.

---

### Post by madrunner on 2008-07-29
Ubuntu 8.04 (Hardy Heron) for me

---

### Post by phidia on 2008-07-29
> **madrunner said:**
> Ubuntu 8.04 (Hardy Heron) for me

If you had a 7.10 livecd it would be interesting to see if it works in that.

---

