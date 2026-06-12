---
title: "Desktop is connected to my televsion.  Extend/Mirror Ubuntu Desktop?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Buttons840 on 2008-11-22
I duel boot Vista and Ubuntu.  I have recently connected my tower to the much larger television.  Vista gave me some trouble, but I figured it out.

Anyways, I start up Ubuntu for the first time, and it's working very smoothly with the 2nd monitor (720p television).  My main monitor supports a higher resolution, and the main monitor was mirrored onto the TV.  The entire desktop thus cannot fit on the television, and rather than "crunch" it down, the TV is showing only part of my main monitor to match it lower resolution.  The part the TV is showing moves around as I move the mouse.

It's really nicely set-up already, and I haven't done anything.  The TV is a pixel by pixel mirror of the main monitor, but a "zoomed in" version if you will; and it's cool how it fallows the mouse around.  I will certainly find use for this display mode in the future.

**This is where I need help.**  How do I change the display mode?  In Vista there was an option to extend the desktop, or to mirror the desktop.  (It's a shame Windows doesn't have a pixel by pixel zoomed in mirror like Ubuntu is doing now.)  How can I extend the desktop onto the 2nd monitor, that is, be able to drag a window from my main monitor over onto the television?

Thank you.

---

### Post by christopher.newell on 2008-11-22
Hi Buttons, I can't help with your Linux mirror/extend issue, but I thought I'd let you know that Windows does offer the "zoomed in" screen that follows your mouse.  ATI calls it a "virtual desktop".  I used it a lot on a laptop with a low-res display when doing vector and raster graphics.  I knew keyboard shortcuts for most of my tools and functions, so I could focus on the graphic at a decent size instead of zooming in and out a lot.  Other than that, I didn't really find it very useful.  As soon as my laptop was upgraded, I stopped using the feature.  At the time, I downloaded it from the ATI website, but it was included with the driver for my home system.  I have nvidia on my work laptop, and it's there, but I can't remember if it has a name.

---

### Post by MunkyJunky on 2008-11-22
If you run an nVidia graphics card, you can set it up in nvidia settings.

```
sudo apt-get install nvidia-settings-manager
```

I'm 95% sure thats the right command, otherwise have a look in synaptic. I'm not on my Ubuntu to be able to check.

---

