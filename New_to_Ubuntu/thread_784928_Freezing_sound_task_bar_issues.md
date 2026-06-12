---
title: "Freezing sound/ task bar issues"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by TwistableLime on 2008-05-06
Ever since I installed 8.04 I've been having freezing issues. Sometimes I'll go a whole day and it will be fine, but other times I will have to shutdown and restart my laptop in order to not only get back my sound which goes out as well but to also get back the ability to use the task bar. 

I'm not sure how well I've diagnosed this problem but it seems to occur when I listen to music through Audacious while on Pidgin and Firefox. It also seems to happen when I have OpenOffice Word Processor, Audacious, Pidgen and Firefox open. What happens is that I'll listen to a song or two and then stop and do some work. Then I'll take a break and try and listen to another song only to have Audacious not play; when I try and open a track or physically click on a song Audacious will open but it will open as if I had only opened the program and not tried to play anything.

Then I'll usually go to website to watch a video to see if its just Audacious or my entire sound and sure enough its my entire sound. Then, in this no sound state, if I proceed to open the colume control it will not open up, and if I try and open a terminal it simply freezes and I must Force Quit. After that my task bars (top and bottom) cease to function. The only way I seem to be able to get my computer back to normal is to hold the power button until it turns off and then restart it. Note though that desktop icons seem to work and I can continue to use Firefox; however just today my Envince Document Viewer would not load and that too resulted in my task bar being frozen.

Perhaps it is a hardware issue; I'm using a an HP dv6000t laptop, dual-core 1.73 GHz processor and 2GB of RAM. Or maybe it is a sound card problem, but since the sound seemed to work right out of the box and since I can get it to work fairly easily I don't think so.

Any suggestions?

---

### Post by Lilibette on 2008-05-07
I am thinking it can't be a hardware issue, because the same exact thing is happening to me.  I just started searching about it and came across this post.  Now I'm gonna go see if anyone's figured anything out.  :/

---

### Post by jeppo on 2008-08-10
Same problem here.  Sound stops working and task bar locks up.  I'm not sure if it is all of those programs, but it is definitely frustrating.

Quick question though.  When you restart your x-server (ie, ctrl+alt+backspace) does it hang when you try to log in again?

Help with this would be great.

Chris

---

### Post by daniel3ub on 2008-10-02
Hi, there.

Having the same problem here. I have a Pavillion DV6000 White, using Ubuntu 8.04.
I use Exaile to play MP3s, and I was thinking it was a Exaile issue. It seems it's not...

If I restart the X server (CRTL+ALT+BACKSPACE) everything comes back to normal.

If I have a terminal window open, it just continues to work fine.

Is there a way to restart just the bars, without restarting the whole server?

For the sound issue, I do the following:
```
sudo /etc/init.d/alsa-utils restart
```
Sometimes it will work (most of the times).

---

