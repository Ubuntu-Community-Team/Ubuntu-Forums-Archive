---
title: "Nouveau driver with nVidia GTX 580"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by Roberto_Perico on 2014-07-20
Hi to everybody,
I'm new in this community and i've installed Ubuntu 14.04 LTS in my assembled PC two days ago. Here's my problem: when i had just installed it, my splash screen was pretty good, it appeared Ubuntu logo in 1920 x 1080p resolution but the system, after about 5 minutes went in crash. So i've installed property driver for my GTX 580. After that my splash screen has become in a low resolution and the Ubuntu logo doesn't appear more. I found a guide that explains how to solve the logo's problem, but for the resolution i've read my GTX 580 native resolution doesn't reach 1080p. So, there is a method to use nouveau driver with my graphic card? i would want my splash screen looks beautyful. It's hurting me. Thank you


PS: sorry about my bad english, i'm a italian guy and i don't speak english every day :)

---

### Post by kc1di on 2014-07-20
Hi Roberto_Perice and welcome to Ubuntu,

[Here is a page ]("http://www.binarytides.com/ubuntu-fix-nvidia-graphics/")that may be of help to you.
The suggestions on [this page]("http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases") worked for me also.

---

### Post by grahammechanical on 2014-07-20
I think that you are confusing High Definition TV video modes with screen resolution.

[http://en.wikipedia.org/wiki/1080p](http://en.wikipedia.org/wiki/1080p)

From the Nvidia specification I see that the GTX580 is capable of a maximum digital resolution of 2560 x 1600 and a maximum VGA resolution of 2048 x 1536. A lot will depend upon the optimal resolution of the screen. Digital monitors store information about their capabilities in their electronics and it is called Extended Display Identification Data (EDID).

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

When Ubuntu loads it reads the EDID and sets the screen resolution from the information stored there. In this way Ubuntu does damage the monitor by running it at the wrong resolution. A graphic adapter might be incapable of running the monitor at the optimum resolution. There is not much we can do about that except buy another graphic adapter. On the other hand the graphic adapter might be capable of giving a greater output but running a monitor at a higher than optimum resolution risks damaging the monitor.

In Ubuntu 14.04 we go to System Settings>Software and Updates>Additional Drivers tab. If we are connected to the Internet and if we wait a little bit the utility will present us with a list of five video drivers. Four of the drivers will be proprietary and one video driver will be open source. We can select either of these drivers and by clicking Apply Changes the utility will replace the present driver with the driver we have selected. This is what I see for my Nvidia GT220 graphic adapter.

X.Org. X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
Nvidia binary driver - version 331.89 from nvidia-331 (proprietary, tested)
Nvidia binary driver - version 331.89 from nvidia-331-updates (proprietary)
Nvidia legacy binary driver - version 304.123 from nvidia 304 (proprietary)
Nvidia legacy binary driver - version 304.123 from nvidia 304-updates (proprietary)

Just select Nouveau and click Apply Changes.

Regards.

---

### Post by Roberto_Perico on 2014-07-20
Thank you for your answer. I think the problem is the VBE. vbeinfo shows that the maximum resolution is 1680 x 1050. If i set the Nouveau driver it crashes, but the bootscreen is in the right resolution.

---

### Post by kc1di on 2014-07-20
There is a problem with nouveau and the current kernels (or it maybe xorg, do not remember) on some machines.  I would advise using the Nvidia driver that corresponds to your card.
you may not be able to get the splash screen any better than 1680x1050 sorry :(

But at lest it will work without crashing. 
The second page I posted above may help some  good luck.

---

