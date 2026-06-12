---
title: "tip: wine, nvidia driver and garbled screens"
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Sambalbai on 2006-08-04
A tip for those who have trouble with setting up wine. I couldn't find anything about this when I was having this problem, so I thought I'd share this:

On my system (Kubuntu Dapper, K7 architecture kernel, Nvidia geforce go 7600), wine and winecfg would give a garbled screen with all kinds of random colours when I ran them. I got it working by selecting the nv driver instead of the nvidia one, restart X server, login and run winecfg. (In winecfg I disabled frame buffering to be sure, but it may be you could leave it on.) After that wine ran fine under the nv driver. I switched back to the nvidia driver and restarted X again. Finally, I put my old xorg.conf back (to get my display resolution settings back). Now wine worked under the nvidia driver too.

Hopes this helps someone.

cheers,
             Sambalbai.

---

