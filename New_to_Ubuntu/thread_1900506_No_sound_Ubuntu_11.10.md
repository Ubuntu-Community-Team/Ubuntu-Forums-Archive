---
title: "No sound Ubuntu 11.10"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by rem1100 on 2011-12-26
I have a Dell Dimension 4700 with dual boot Ubuntu 11.10 and Windows XP. The sound does not work with Ubuntu. Any help getting the sound to work on Ubuntu would be appreciated.
Thanks
Jeff

---

### Post by cavh on 2011-12-26
See if this helps:

[https://help.ubuntu.com/11.10/ubuntu-help/sound-nosound.html]("https://help.ubuntu.com/11.10/ubuntu-help/sound-nosound.html")

---

### Post by rem1100 on 2011-12-26
Got it to work thanks,
Jeff

---

### Post by khelben1979 on 2011-12-26
According to [the technical specifications]("http://support.dell.com/support/edocs/systems/dim4700/sm/specs.htm#wp1043338") which describes your hardware, you should have ADI 1980 AC97 as sound device.
Can you check that up? ( run **lspci** from a text terminal such as [xterm]("http://en.wikipedia.org/wiki/Xterm") )

Then if that's true, the so called ALSA (the sound system in Linux) haveto be able to identify your sound chip/card.

The sound driver often exists inside your Linux kernel, which means that ALSA should automatically detect it if it's there. If the [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") application reports that it's there, then you got the hardware support there, but something isn't configured correctly so it cannot be used, such as the volume bar, mute button etc etc, check the link from the previous poster..

---

