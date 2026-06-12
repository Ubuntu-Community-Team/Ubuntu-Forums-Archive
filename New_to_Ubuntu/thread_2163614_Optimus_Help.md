---
title: "Optimus Help?"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by tysonhemelstrand on 2013-07-19
So, After the living hell it was trying to get my GT 630m Running on 12.10, I eventually gave up. Now that we have 13.04 AND official optimus support from NVIDIA, I was wondering if anyone could provide me with a comprehensive walkthrough on getting Optimus working on Ubuntu 13.04. I would prefer switchable graphics to be functional (Not sure if you still need bumblebee for that), But as long as my NVIDIA GPU is being used as the primary renderer, I suppose that would work. Sorry about the noobism, really trying to get into Ubuntu after Valve's Steam support for Linux - the reasons to go for it just keep piling up. Thanks in advance!

FYI, I have a GeForce GT 630m and an Intel HD Graphics 4000 card. I can't disable the intel graphics in the bios.

---

### Post by mastablasta on 2013-07-19
> official optimus support from NVIDIA huh? what official support? 

bumblebee is the thing that is needed.

edit: i see they added basic support in beta drivers...

---

### Post by oldfred on 2013-07-19
I do not have Optimus, but thought it needed the very newest Linux kernel which is only with 13.10.

 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)
The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working


 Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by borzwazie2 on 2013-08-05
To my knowledge (and it may be wrong!) getting the proper support for xrandr, multimonitor, and Optimus is going to take kernel 3.9, xrandr 1.4, and a tweak or two for the intel drivers, along with these nVidia drivers. I spent quite some time trying to get all these things to work, to no avail. I did get multimonitor working at one point, using bumblebee/Optimus - but just try to undock and see what happens :P

I'd be happy to be corrected here.

EDIT: This stuff *almost* works with the Intel and Nouveau drivers, out-of-the-box - but not with xrandr, so no undocking :(. If you install 13.04, with your laptop in Optimus mode, and docked, you can get three screens, and it mostly works (there are bugs, and the screens tend to corrupt). However, if you undock, X loses it's tiny little mind, and only a reboot will bring it all back (for me, anyway).

---

