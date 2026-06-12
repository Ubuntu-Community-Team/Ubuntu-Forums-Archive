---
title: "[HELP] Why no sound after kernel upgrade?"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by protoss96 on 2013-08-07
Hi,

I am currently running Ubuntu 10.04 LTS Lucid, why that version? Because it fits my hardware. My kernel version is:
```

aleksandar@aleksandar-aspire:~$ uname -r
2.6.32-50-generic

```
Here is tut for kernel upgrade, [http://www.upubuntu.com/2013/07/installupgrade-to-linux-kernel-3102-in.html](http://www.upubuntu.com/2013/07/installupgrade-to-linux-kernel-3102-in.html).
And when i wanted to upgrade linux kernel to a 3.10.2 everything works fine but after reboot, i have no sound, neither on headphone neither on front speaker.
Now i have backed up my old kernel 2.6.32-50-generic.
I have acer Aspire 9500 typical notebook for school works, maybe that helps, and of course sound card is Intel HDA.
I also tryed alsamixer for disabling auto-mute but that doesn't working, also i tryed pulseaudio -k or killall pulseaudio.

Thank you so much for every helpful reply. :mrgreen:

---

### Post by protoss96 on 2013-08-07
Ah yes, I have upgraded to 3.0.0 and its working fine, but what about higher versions?

---

### Post by xtdv on 2013-08-07
Did you try to run alsamixer as root?
```
sudo alsamixer
```

I'm using kernel 3.5.0-37-generic and sound works fine.

---

