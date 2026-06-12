---
title: "SDL: No available video device after opening TuxRacer..."
date: 2008-01-09
forum: Packaging and Compiling Programs
---

### Post by rosiny on 2008-01-09
So, I've made a program that utilizes SDL audio and video, and the program in fact, worked completely normally and beautifully until I decided to download tuxracer to play for fun, and immediately after, the program stopped working, giving me the error that a video device could not be found... could someone help me free up my video device for use by this program? I've looked at other "solutions" to this problem but none of them work. 

I've attempted:
- recompiling... and running again
- running the program on a friend's ubuntu computer by sshing to his IP (it works, and a video GUI shows up on MY computer, as expected)
- reinstalling my SDL packages
- disabling compiz, running metacity
- restarting the gdm
- using older xorg.conf files

If anyone could help that would be amazing. All that SDL video's function right now is to display ONE image. There is no complexity, but this error still occurs.

Thank you!

---

### Post by rosiny on 2008-01-10
Okay. This problem was solved. I reconfigured my xorg.conf, installed the xorg-dev and xserver-xorg-dev packages, and reinstalled the newest version of SDL. Strange how that worked out...

---

