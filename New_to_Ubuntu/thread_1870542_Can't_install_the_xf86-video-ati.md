---
title: "Can't install the xf86-video-ati"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by frohfroh on 2011-10-27
Hi,
It's my second day using Linux(Ubuntu 11.10 Wubi) and I noticed that my laptop is struggling to play videos. I found out that my video card is supportes by the X.org driver xf86-video-ati ant tried to install it, but without success. I downloaded the driver from [http://cgit.freedesktop.org/xorg/driver/xf86-video-ati](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati), but when I try to autoconf I get the the error message:
configure.ac:34: error: must install xorg-macros 1.8 or later before running autoconf/autogen
So I tried to find xorg-macros and the closest thing I could get was [http://cgit.freedesktop.org/xorg/util/macros/](http://cgit.freedesktop.org/xorg/util/macros/)
So I installed it, but the problem persists. 
The package name is util-macros. Can someone please tell me what I am doing wrongly?

---

### Post by mcduck on 2011-10-27
You already have the opensource Ati driver, Ubuntu will use that by default. No need to do anything about it.

If you want to try a more up-to-date version (although there probably isn't one much more up-to-date than what's used on 11.10 already) you might want to use some PPA repository instead of trying to compile the driver yourself. For example the [ubuntu-x]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") and [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") provide new driver versions for Ubuntu (notice the warnings about xorg-edgers currently breaking Unity).

---

### Post by frohfroh on 2011-10-27
Thank  you, 
i am so glad I don't have to do anything else! But how can I be sure that I have the opensource ATI driver? I'm asking because I had a significant drop in performance when playng videos since I changed to Ubuntu, and when I see system information I see:
Driver:Unknown 
Experience:Standard
I'm not sure if it is important at all but the video card in question is a Radeon XPRESS 200(M).

---

### Post by mcduck on 2011-10-27
One smooth way of checking what driver you are currently using is opening a terminal and running the following command:
```

glxinfo | grep renderer
```
(this command should show "Gallium 0.4" + your GPU's model when running the open-source driver)


You can also run "lspci -v" to see all the details of your graphics card, including the kernel driver it's using. It should be listed as "VGA compatible controller" and you should, by default, be using the "radeon" driver. Which is exactly the same as the "ati" driver in the link you posted.

---

### Post by frohfroh on 2011-10-27
Thank you so much!

---

### Post by mcduck on 2011-10-27
No problem. Although this of course didn't help with your video playback performance... Which is quite strange, as far as I know the open-source driver should have rather good support for the Radeon Xpress 200M.

However it isn't very new GPU, and wasn't too powerful even when it was released. Perhaps it's just working too hard to sustain the GPU-accelerated desktop to have enough power to handle video playback as well? You might want to try if you get better performance when using Unity2D, Gnome-shell's fallback mode or some alternative desktop environment that doesn't use GPU acceleration. That would of course mean sacrificing some of the pretty effects, but I suppose smooth video playback would be more important...

---

