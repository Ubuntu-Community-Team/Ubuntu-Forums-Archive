---
title: "problem with sound in hardy heron"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by bovier on 2008-06-07
the problem is the following: 
sound either works for skype and flash (haven't tried other applications), or, it works for playing mp3 or mp4 (in any program: vlc, totem). That means that after I have used skype or watched a video on youtube, I cannot play any music, and if I have played music, I cannot watch any flash or talk on skype. After reboot, both options are free to choose from again.

tried to see if other had this problem, but i didn't found anything

---

### Post by Joshua Netterfield on 2008-06-07
> **bovier said:**
> the problem is the following: 
sound either works for skype and flash (haven't tried other applications), or, it works for playing mp3 or mp4 (in any program: vlc, totem). That means that after I have used skype or watched a video on youtube, I cannot play any music, and if I have played music, I cannot watch any flash or talk on skype. After reboot, both options are free to choose from again.

tried to see if other had this problem, but i didn't found anything

This is now a very famous issue on the forums.

See [http://ubuntuforums.org/showthread.php?t=808710&highlight=flash](http://ubuntuforums.org/showthread.php?t=808710&highlight=flash)

---

### Post by bovier on 2008-06-07
> **Joshua Netterfield said:**
> This is now a very famous issue on the forums.

See [http://ubuntuforums.org/showthread.php?t=808710&highlight=flash](http://ubuntuforums.org/showthread.php?t=808710&highlight=flash)

thanks for your reply. 
however, my sound does not start to work again after I have closed firefox. I installed libflashsupport, but it didn't help. (actually, after starting up my computer this time, I haven't watched any flash video's. I am just using skype right now, but mp3 in totem won't start. (he says "playing", but the time remains on 0:00)

---

### Post by markbuntu on 2008-06-07
I never had any luck with libflashsupport myself. I also never had any luck trying to use firefox3b5 so I got 3.0rc1 and dumped libflashsupport and that fixed a lot of my problems with firefox and flash.

One thing you can do as an expedient. If you have a system monitor running you can use that to kill flash and firefox after you use them because they dont always release the resources they use, even when they are sleeping. Killing them is the only option sometimes.

It seems that pulseaudio has some unfindable bug that also causes some problems. Once I got away from pulseaudio and switched all my sound preferences to alsa instead of automatic I have had far less problems with kernel panics and sound availability.

Even with that, I always have to restart my music player after using flash.

I dont use skype so I know nothing about that but I suspect the issue with sound is very similar.

Rebooting should be totally unecessary.

---

