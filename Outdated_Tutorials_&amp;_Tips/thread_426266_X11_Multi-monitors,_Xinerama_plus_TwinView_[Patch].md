---
title: "X11 Multi-monitors, Xinerama plus TwinView [Patch]"
date: 2007-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by travlr on 2007-04-28
Those of us who use multi-monitors can't wait for xorg and video card manufacturers to catch up to our multi-tasking, multi-monitor needs. 

If you want more than two monitors (and/or tv-out) you are basically stuck with xinerama which is not as an ideal solution as we'd like it to be. TwinView is lower-level compared to the xinerama layer, but it's limited to two monitors, (doesn't even allow tri-head/tv-out). 

Xinerama does allow Twinview as a "sub-layer" but then the problem is, is that xinerama doesn't not respect Twinview's display sectioning (since it's a single card, xinerama only respects it as a single display. So, when you click the "expand" window button it spreads across all of the two monitors. PAIN IN THE ***!

[[COLOR="Blue"]_Bernhard (jaXXon), over on the nvNews forums fixed this problem_[/COLOR]](http://www.nvnews.net/vbulletin/showthread.php?t=85604) with a simple hack to the xserver-xorg-1.1.0 source that I hope xorg will soon adopt. I applied his nifty work to xserver-xorg-core-1.2.0 which is the second -p1 patch supplied below. 

When I have some more time in the next few days I'll provide step by step instructions for downloading the ubuntu source, applying the patch, and installing it in your box through 'dpkg -i'. Also see Bernhard's post labeled #10 in the nvNews thread I linked to up above.

-Dieter

---

### Post by discunit on 2009-03-07
For those interested in multi monitor setups , you can use the Monitor Plus from XEO. For those of you interested, their site is
[www.xeo.eu ]("http://www.xeo.eu")
I use 3 monitors. Works great!

---

