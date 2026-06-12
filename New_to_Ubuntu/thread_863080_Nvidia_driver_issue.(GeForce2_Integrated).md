---
title: "Nvidia driver issue.(GeForce2 Integrated)"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by phantomreaper on 2008-07-18
It's been a long time since I've been here...been trying different Linux distros...

PC Specs:
1.66 AMD Athlon 2000+
nVidia GeForce2 Integrated
512MB RAM
D-Link DWL-G510

Link to my Xorg log.

[http://www.alistor.co.cc/files/Xorg.0.log](http://www.alistor.co.cc/files/Xorg.0.log)

Here's my dilemma;

I installed Ubuntu 8.04 off the Live CD, then installed the restricted nVidia driver. Restarted my computer and a dialog box pops up saying, "Cannot recognize your driver", so I chose my card manually from the list...and when I'd applied the settings, the computer just hangs at a black screen. Restarted the computer and it loads into Ubuntu, using Ubuntu's default driver. I set the nVidia driver as enabled, restart, hangs on black screen. Went in recovery mode and reconfigured Xorg. Now I'm stuck, really confused, been surfing google trying to find out how to fix this without any luck. 

Thanks in advance :)

---

### Post by overdrank on 2008-07-18
> **phantomreaper said:**
> It's been a long time since I've been here...been trying different Linux distros...

PC Specs:
1.66 AMD Athlon 2000+
nVidia GeForce2 Integrated
512MB RAM
D-Link DWL-G510

Link to my Xorg log.

[http://www.alistor.co.cc/files/Xorg.0.log](http://www.alistor.co.cc/files/Xorg.0.log)

Here's my dilemma;

I installed Ubuntu 8.04 off the Live CD, then installed the restricted nVidia driver. Restarted my computer and a dialog box pops up saying, "Cannot recognize your driver", so I chose my card manually from the list...and when I'd applied the settings, the computer just hangs at a black screen. Restarted the computer and it loads into Ubuntu, using Ubuntu's default driver. I set the nVidia driver as enabled, restart, hangs on black screen. Went in recovery mode and reconfigured Xorg. Now I'm stuck, really confused, been surfing google trying to find out how to fix this without any luck. 

Thanks in advance :)

HI and you may look at how much memory is being shared with the graphics in bios as this may cause some issues.

---

