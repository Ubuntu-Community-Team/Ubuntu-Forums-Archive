---
title: "matlab &amp; nvidia in feisty"
date: 2007-04-24
forum: Programming Talk
---

### Post by Rumo on 2007-04-24
Since an upgrade during the feisty development process, the fonts in matlab got really tiny - even 48 pt are barely readable.
 
 I now tracked down the problem to the nvidia-glx driver. If I use the non-accelerated open-source nv driver everything is fine. I would like to have 3d acceleration, though (maybe I'll use the intel graphics which is on my mainboard, too).
 
 Since this is a problem of a proprietary package I'm not sure where to post a bug report (launchpad, mathworks, nvidia?). Can anyone help?

---

### Post by the_dark_light on 2007-04-24
Your best bet would be to try to find out if NVIDIA have a bug reporting facility/feature

I haven't been able to find one on the NVIDIA site, but that being said I've only quickly browsed.  NVIDIA do mention this site:

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

as being useful for fault-finding.

As this seems to be a bug with the NVIDIA driver, I still think that NVIDIA will be your best bet (how else can we expect them to rectify the many problems/annoyances with their driver)

---

