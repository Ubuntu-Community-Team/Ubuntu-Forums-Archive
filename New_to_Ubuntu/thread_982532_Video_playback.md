---
title: "Video playback"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by tanha on 2008-11-14
I upgraded from 8.04.1 to 8.10. Video worked fine in 8.04.1. Now, when there are "fast" moving sequences, choppy lines cut through the video. Any ideas what happened; how to fix it (besides downgrading)?

Thank you.

---

### Post by taurus on 2008-11-14
Which media player you are using to view your video files?

---

### Post by Bölvaður on 2008-11-14
double post

---

### Post by Bölvaður on 2008-11-14
does it happen on every moving thing? (windows, flash video, opengl.. like games)

---

### Post by tanha on 2008-11-14
> **taurus said:**
> Which media player you are using to view your video files?

VLC and Totem. Any video.

---

### Post by agwblack on 2008-11-23
I have this same problem. Things like youtube work fine, but when I try to play video files on Totem or VLC, the picture flickers loads. I have found that switching my appearance settings to "none" eliminates the problem, but I would prefer if there was another solution that allowed me to keep some of the visual effects as well. I am using a ATI Radeon HD 3450. Has anyone got any suggestions, bearing in mind that I am very new to Ubuntu and Linux in general?

Thanks in advance.

---

### Post by tanha on 2008-11-23
> **agwblack said:**
> I have this same problem. Things like youtube work fine, but when I try to play video files on Totem or VLC, the picture flickers loads. I have found that switching my appearance settings to "none" eliminates the problem, but I would prefer if there was another solution that allowed me to keep some of the visual effects as well. I am using a ATI Radeon HD 3450. Has anyone got any suggestions, bearing in mind that I am very new to Ubuntu and Linux in general?

Thanks in advance.

Thanks for the suggestion. But, I don't use desktop effects. I have an integrated Intel graphics card.

---

### Post by agwblack on 2008-11-25
*BUMP* Some help on this would really be appreciated.

Thanks in advance

---

### Post by whitethorn on 2008-11-25
Hi, I'm not really sure what the problem is.  Could you install mplayer and see if you still get the same problems with it?

```
sudo apt-get install mplayer
```

Then start some video you know you've had problems with, and when the video is playing and you have the active video in front of you click on the letter "d" until you see framedropping enabled.  

If this works (you don't get as many lines and whatnot) then it's a problem with your computer not rendering the video and sound tracks together at the same time.  

There's probably some option in VLC to enable frame dropping, not quite sure where though.  If this doesn't help then play around with the video output formats.

@ agwblack Highjacking a thread isn't exactly nice.  Try different video output formats (or get different drivers for you graphic card) Opengl + compiz doesn't always work well together.

---

### Post by agwblack on 2008-11-26
> **whitethorn said:**
> @ agwblack Highjacking a thread isn't exactly nice.  Try different video output formats (or get different drivers for you graphic card) Opengl + compiz doesn't always work well together.

Apologies, I'm very new, not fully aware of etiquette and so on. Thanks very much for your help though.

---

