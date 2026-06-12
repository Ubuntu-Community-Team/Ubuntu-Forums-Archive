---
title: "Ubuntu Will Not Allow Me to Set Multiple Monitors"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by jcobban on 2013-01-18
I am running Ubuntu 12.10.  I have two displays on my computer: the builtin screen of the laptop and a television attached through HDMI.  I go into the Displays setup panel and turn off mirroring, but when I attempt to apply the configuration I get the message:

required virtual size does not fit available size: requested=(2560, 768), minimum=(320, 200), maximum=(1600, 1600)

How do I change the maximum?

---

### Post by jcobban on 2013-01-18
> **jcobban said:**
> I am running Ubuntu 12.10.  I have two displays on my computer: the builtin screen of the laptop and a television attached through HDMI.  I go into the Displays setup panel and turn off mirroring, but when I attempt to apply the configuration I get the message:

required virtual size does not fit available size: requested=(2560, 768), minimum=(320, 200), maximum=(1600, 1600)

How do I change the maximum?

When I looked at the specified maximum I realized that if I stacked the 2 monitors one on top of the other, rather than side by side, they would fit within the specified maximum dimension.  So I got this to work without changing the maximum.

---

### Post by helpee on 2013-01-18
Way to think outside the screen ;)

---

