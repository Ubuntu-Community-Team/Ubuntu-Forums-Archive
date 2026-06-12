---
title: "X server problem"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by nhasan on 2008-10-11
Hi, I am running into a problem with my display with Ubuntu any help is most appreciated. I am somewhat familiar with unix as an end user but not at all with the X-windows so please bear with me

I had Ubuntu (6.06.1 LTS upgraded) running on my desktop (dual boot) and did not use if for a while. In the mean time I switched the video card and the monitor. The video card I went to is a Nvidia 76000GT and the monitor an Optiquest Q2162wb. 

Now, when I boot into Ubuntu I get a blue screen stating there is a problem with X Windows (on tty2). On tty2 here is just a blinking cursor, I tried a crtl-alt-backspace, ctrl-C and ctrl-Z to no effect

I looked at the log files at /var/log/Xorg.0.log and found some advice on these forums to run dpkg-reconfigure xserver-xorg several times and but the monitor is not autodetected. I tried different options (following the settings advised by the monitor's manual around sync rates) but to no effect. 

Please help.

Thanks!

---

### Post by eternalnewbee on 2008-10-11
Could you post a thumbnail of the blue screen?
I remember something similar with my system and as I recall the error occured because I had set the resolution too high for my monitor. Try rebooting in safe mode and adjusting your screen resolution. That's the only thing I can think of.
Good luck.

---

### Post by eternalnewbee on 2008-10-12
Well, nhasan...
Any luck?..
Please post a reply so we know if it worked or not...

---

