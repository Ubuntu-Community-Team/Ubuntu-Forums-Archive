---
title: "[SOLVED] How to uninstall NVIDIA driver from prompt?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by gldearman on 2008-09-06
Hi,

I just installed Hardy. I have an NVIDIA Geforce 4 MX420 video card.  Upon installation, Hardy seemed to recognize it just fine.
The first thing I did on the new system was run update manager and install all of the updates (including an update to the Linux kernel).

After that (and an obligatory restart), I got a notification that a proprietary driver was available for my video card, and that I would not be able to enable visual effects without it.  So, I downloaded and installed the driver (nvidia glx).

Upon restart, I am unable to get **any** display.  When Ubuntu finishes loading, my monitor goes idle and my screen goes dark.  There appears to be nothing to do but hard reboot the system.

So, I need to now how to properly configure this driver or else remove it from recovery mode.  I'd just like to get back to where I was before I installed the driver, so that I can at least boot Ubuntu!  Then, I'll worry about making the video card do what I want it to do.

Thanks

---

### Post by wolfen69 on 2008-09-06
```
sudo apt-get purge nvidia-glx-new
```

---

### Post by arochester on 2008-09-06
Don't boot into your normal kernel. Boot into Recovery. It now has an option "Try to recover XServer. Use that.

---

### Post by gldearman on 2008-09-06
> **arochester said:**
> Don't boot into your normal kernel. Boot into Recovery. It now has an option "Try to recover XServer. Use that.

Thanks.

That worked great.

Now to see if I can get the video card to actually do what I bought it to do ... but that's another problem.

---

