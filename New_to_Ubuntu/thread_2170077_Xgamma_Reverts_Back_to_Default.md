---
title: "Xgamma Reverts Back to Default"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by aehainsworth on 2013-08-24
Hey all! 

I'm a newcomer to Ubuntu, having installed it only last week (followed the Easy Linxu Tips guides and everything). I'm loving it so far! It's really gorgeous and it just runs so smoothly.

However, there is a minor quirk that annoys me somewhat. The screen is looking a tad too bright and my monitor's settings are fine. So I had been using the xgamma tool to lower the gamma to .700, which makes everything look so wonderful. It worked fine on the day of the installation. But! It has reverted back to 1.000 ever since. I would run the xgamma command and see the difference for all of one second before it gets so washed out again.

I'm using an Nvidia card and originally, it was using the default open-source driver. I changed it to the most recent and stable proprietary driver shortly after the installation. After having lurked on here for some time, I eventually thought it was because of the driver, so I switched back to the open-source driver to no avail. 

Any suggestions? And please keep the tech-speak to a minimum. If you can keep it straightforward, I would greatly appreciate it. Thanks!

---

### Post by alarme on 2013-08-24
Hi:

If using propietary driver, try nvidia-setting applet and confirm changes.
Look at "X server color correction"

Cheers

---

### Post by aehainsworth on 2013-08-24
> **alarme said:**
> Hi:

If using propietary driver, try nvidia-setting applet and confirm changes.
Look at "X server color correction"

Cheers

I tried that and got the same result. However, I got curious about the f.lux applet I was using, so I turned it off and lo behold, the gamma didn't auto-revert. I wonder why that is. I thought the applet was supposed to work in conjunction with the monitor's gamma and it'd only change with the time of the day. Hmm.

---

