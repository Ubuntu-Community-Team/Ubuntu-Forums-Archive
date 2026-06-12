---
title: "getting 5.1 surround sound to work on ubuntu"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-26
I tried it on windows and it works perfectly. When I try it on here, only my front left and front right speakers work. I've tried several tutorials, but they always tell me to edit some file that I just don't have. any ideas?

---

### Post by Tim Sharitt on 2008-07-26
I don't really know how to help, but have you tried this: [http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")?

---

### Post by yufei on 2008-07-26
test

---

### Post by adobrakic on 2008-07-26
> I don't really know how to help, but have you tried this: [http://ubuntuforums.org/showthread.php?t=795525?](http://ubuntuforums.org/showthread.php?t=795525?)

No, but i'm kind of hesitant because pulse audio only allows me to have sound in one program at a time. The files that I don't have are asoundrc or whatever, and I can't remember the other one. I could probably just create them, but I don't know how to do that hah. 

> 
test

..you serious?

---

### Post by adobrakic on 2008-07-28
Pulse Audio trick didn't do it. Is there a tutorial for alsa?

---

### Post by Shazaam on 2008-07-28
Have you looked at the alsamixer settings? Open terminal and enter this...
```
alsamixer
```
Anything that has an "M" under it is muted. Highlight the settings and click your m key to unmute. Scroll to the right to get to more settings if your card supports them.
pulseaudio was a problem for me so I went to System>Preferences>Sound and changed everything to alsa as default.

---

### Post by adobrakic on 2008-07-28
I've looked at this, but I don't have any options for the surround sound channels.

---

