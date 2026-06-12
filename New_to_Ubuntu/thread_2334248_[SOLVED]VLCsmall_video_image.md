---
title: "[SOLVED]VLC/small video image"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by xedoc on 2016-08-17
Hello,

When i play a video with the default media player in Ubuntu, the videos plays as it should. No errors, full screen etc...

I installed VLC because i prefer VLC but the issue is, when i put the video in fullscreen, the video is very VERY small. I assume it's not codecs otherwise the other player would do the same.

Any ideia what could be ?

Kind regards,

---

### Post by mc4man on 2016-08-17
Try Vlc > Tools > Preferences > Video > Output - pick an output good for your hardware, likely either Opengl GLX or Xvideo 
(unless using vdpau hwdec, then use vdpau

Also maybe go to the Input/Codecs tab > Hardware-accelerated..  > either pick proper or just disable.
Save edits.

The point being don't leave either on the Default of Automatic

---

### Post by xedoc on 2016-08-18
Hi mc4man,

Thank you for your help. It worked by changing to Opengl GLX. 

Kind regards,

---

