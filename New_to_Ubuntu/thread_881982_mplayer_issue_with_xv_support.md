---
title: "mplayer issue with xv support"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by aestrivex on 2008-08-06
this morning ubuntu decided not to load properly, so i went in to recovery mode and used the option there to reset X (as well as the other options).

long story short, it worked and ubuntu loaded again.

however, subsequently (and obviously i have tried rebooting) when i try to open videos in mplayer i get the following message

```

[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.

```


mplayer still works with other vo devices.

however, xv works better for a variety of reasons; how do i fix it?

---

### Post by aestrivex on 2008-08-06
ah... this could be a problem.

i attempted to enable the nVidia driver which had been disabled, and again the computer hung upon initialization of ubuntu.  this is potentially a serious video card problem.

---

