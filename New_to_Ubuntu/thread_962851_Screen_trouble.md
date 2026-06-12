---
title: "Screen trouble"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Manillien on 2008-10-29
Hello,

I have now successfully managed to install Ubuntu Hardy on my PC. I did some updates, installed the Nvidia driver, and everything seems to be running smoothly. However, the next time I boot, the screen flashes between some boot information ("starting blabla" and so on) and a totally black screen, before the GUI starts. Then, I get a message that Ubuntu can't find my screen or graphic card driver, and it has to run in safe graphics mode. When I try to start Nvidia X Server settings, it says that I do not appear to use the Nvidia X driver, and that I should run nvidia-config. 

I tried, and I tried other stuff, like EnvyNG. It seems to me that the problem isn't the driver, but rather, it doesn't recognize the screen. Here's the contents of the /etc/X11/xorg.conf file uploaded.

---

### Post by phidia on 2008-10-29
What model nvidia card do you have? 8 & 9 series cards have had some problems, but then so have other card models since the new xorg in hardy, or intrepid.

That looks like the new xorg since it's very abbreviated.

See the guide on xorg [here]("https://help.ubuntu.com/community/Video").

---

### Post by Manillien on 2008-10-30
Yeah, it's probably the new xorg. However, I couldn't find much that helped with my problem. I tried changing the monitor and card driver manually at startup, when I get the option to configure, but it didn't help. Now, when I do Screen resolution setup, it doesn't know what monitor I have, even though I specified it. What is strange about this is, that the first time I booted, it worked. The next time, it didn't. Strange.

Edit: It's Nvdida geforce 6800 by the way.

---

