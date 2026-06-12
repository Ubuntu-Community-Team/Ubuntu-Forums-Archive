---
title: "video and music problem after watching youtube videos"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Falc7 on 2008-09-15
Whenever i watch a youtube or google video movie, if afterwards i want to watch .flv, .ogg, or seemingly any other sort of video or music file, it won't play normally.
If it is a music file, the progess bar will move, but no sound. If it is a video file, the video will play, but the FPS will be terrible, and no sound.

I have to log out and log back in if i want to fix it

---

### Post by Tatty on 2008-09-15
Try installing

```
sudo apt-get install libflashsupport
```

This should fix flash sound problems in hardy.  Have a read of this page for more info: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by Falc7 on 2008-09-15
yep, fixed, thanks very much :)

---

### Post by lovinglinux on 2008-09-15
Works for me too. Thank you.

---

### Post by Falc7 on 2008-09-15
While it has fixed that problem, it seems to inadvertently caused another one, now when i play AOM through wine, after i have watched a youtube video, i get the message that the game has to proced without sound becuase no sound hardware is avalible, or something similar. Again, logging in and logging out stops the message. Can this be fixed?

---

### Post by Falc7 on 2008-09-18
Anyone know how to stop this solution interferring with wine's programs sound?

---

### Post by TheLions on 2008-09-18
check here to fix PulseAudio:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by billgoldberg on 2008-09-18
Remove libflashsupport asap.

There is a reason that isn't a depenency for flash in Ubuntu.

It will make the whole things extremely unstable. With lots of firefox crashes as a result.

--

To fix this error you will need to switch from PulseAudio to Alsa.

Navigate to "system -> preferences -> sound" and pick Alsa for everything.

-> Problem solved, but you don't loose any stability.

--

Now, it could be that you'll want to upgrade to Flash player 10 RC2, link:

[http://linuxowns.wordpress.com/2008/09/15/new-flash-player-10-rc/](http://linuxowns.wordpress.com/2008/09/15/new-flash-player-10-rc/)

It isn't a final product yet, but I haven't gotten any real problem. Full screen playback in flash 10 is a lot better than in flash 9. It's smoother and requires less cpu power.

---

### Post by Falc7 on 2008-09-20
thanks guys that worked great, flash 10 does seem much better

---

### Post by Falc7 on 2008-09-21
Will i automatically get the Flash 10 RC3 or Flash 10 v1, when they come out?

---

### Post by TheLions on 2008-09-21
no, you'll have to download it manually

---

