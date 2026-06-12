---
title: "New Monitor..."
date: 2011-11-18
forum: New to Ubuntu
---

### Post by sillyboy on 2011-11-18
I am in need of a new monitor that is Linux friendly.  I have a Nvidia Geforce FX5500 video card.  Was thinking a 18.5" model, so as not to over tax the Video card.  I got tired of looking for a monitor that has Linux drivers. I tried a HP S2031 monitor and it did not work out.  The resolution would not hold to 1600X900 when I rebooted the U-Box.

Any help is greatly appreciated.  Thanks

---

### Post by 3rdalbum on 2011-11-18
Monitors communicate with the graphics card, not the OS directly. There's no such thing as a "monitor driver". Any monitor should be able to work with your graphics card, but if you already have an Nvidia driver installed you might need to reinstall it or re-create the xorg.conf otherwise the silly Nvidia driver will assume you're still using the old monitor.

If you're really concerned, take your computer into a store where they have monitors on display and try some out. Plug in the monitor via the DVI port, not the VGA port; it will make it easier for Xorg to detect the specifications of the monitor and pass that to the graphics card.

---

### Post by fantab on 2011-11-18
> **sillyboy said:**
> I am in need of a new monitor that is Linux friendly.  I have a Nvidia Geforce FX5500 video card.  Was thinking a 18.5" model, so as not to over tax the Video card.  I got tired of looking for a monitor that has Linux drivers. I tried a HP S2031 monitor and it did not work out.  The resolution would not hold to 1600X900 when I rebooted the U-Box.

Any help is greatly appreciated.  Thanks

I have always thought that **Monitor is OS independent**. And that Graphics and Video depended on Graphics Card. Its just that I am not 100% sure.

Now, in my case I use Samsung SyncMaster 1920x1080, and it works without any issue. I also have AOC LM75 1280x1024 which in Ubuntu does not get recognized and the resolution is downgraded to 1024x768 by default and I have to force 1280x1024 resolution with xrandr.

---

### Post by sillyboy on 2011-11-19
> **fantab said:**
> I have always thought that **Monitor is OS independent**. And that Graphics and Video depended on Graphics Card. Its just that I am not 100% sure.

Now, in my case I use Samsung SyncMaster 1920x1080, and it works without any issue. I also have AOC LM75 1280x1024 which in Ubuntu does not get recognized and the resolution is downgraded to 1024x768 by default and I have to force 1280x1024 resolution with xrandr.

Thank You!!

---

