---
title: "Sound level not remembered after shutdown/restart"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by jmriverofernandez-4 on 2014-05-26
I'm using Ubuntu 14.04 and the sound level always starts at 100% when I turn on the computer (or at the level that I choose in the lightdm login screen). Is there a way for the sound level of the previews session to be remembered in the new session?

---

### Post by LastDino on 2014-05-26
I can't tell you with certainty that this will work for you or not but it did work for me on my Xubuntu 14.04 fork.  It was starting at 100% sound level as well. Btw, it is well known bug and existed since 2008
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/204536](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/204536)

Open your terminal and type

```
alsamixer
```

That should open sound settings in terminal itself. Adjust appropriate volume levels low (below white section on bars).

Then generate new config by typing this commands and entering one by one.

```
cd ~/.config
```

```
mv pulse pulse-bak
```

```
pulseaudio -k
```

Then see if it is working for you not. 


There is also GUI option available for alsamixer in Ubuntu software centre, I installed that as well and played around settings. I suggest you do the same as I'm not sure if this is a reproducible solution since that was the only time I actually came across this bug. My Ubuntu 13.10 and official Xubuntu 14.04 were working normally, so.. :p

---

### Post by jmriverofernandez-4 on 2014-05-26
Will that make that the sound volume is remembered from the last session? For example if I leave the volume at half when I shut down the computer, will it start at half when I turn on the computer?

---

### Post by LastDino on 2014-05-27
It did for me. I'm able to save my sound settings from last season, I believe that is the back-end of the problem ''system always starting with 100% volume''. But like I said, I can't guarantee you if this will work for you or not. If you could just read that launchpad bug report page, you will notice that there isn't any 100% workable solution mentioned there either. After googling for around 20min I had to play with settings for 10 min and restart my PC 5-6 times during whole process before it finally worked for me.

---

### Post by jmriverofernandez-4 on 2014-05-27
I did what you said, but it just works one time when I restart (the volume at the login screen is the same as it was in the last session, but only for that time), then I'm back to square one, and again, if I change the sound volume in the session, when I reboot the volume is not saved. To change the starting sound volume I need to directly change the sound volume at the login screen.
In other words: changing the volume in the session doesn't affect the volume in the login screen, but changing the volume in the login screen does affect the volume in the session.
What I want is that the volume from last session is saved every single time, so if, for example, I leave in mute the session, next time I start the computer it will also be in mute.

---

### Post by LastDino on 2014-05-28
Keep playing with the settings of alsamixer, that is all I can say on that as it is working for me.

---

