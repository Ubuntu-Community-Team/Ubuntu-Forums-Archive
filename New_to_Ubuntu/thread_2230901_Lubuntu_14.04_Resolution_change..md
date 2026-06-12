---
title: "Lubuntu 14.04 Resolution change."
date: 2014-06-21
forum: New to Ubuntu
---

### Post by gnosis2 on 2014-06-21
Hi. I'm having trouble getting my resolution to my monitors native resolution. I've tried commands using xrandr and sudo and such but they didn't have much affect. I'm running Lubuntu 14.04 and i am using my Nvida Geforce Fx 5200 graphics card. Any help will be much apreciated :P.

Gnosis.

---

### Post by bapoumba on 2014-06-22
Well, I'll be interested too, as for someone else computer, I could not solve this issue, either with the nouveau driver or the nvidia one. The resolution was stuck at 1280x720 while the monitor used to use higher ones. I've tried many things (and spent several hours), xorg.conf was the only file I did not want to get into. Surprisingly, as I had decided to wait a bit before working on that again, the person told me it had "fixed itself" which I do not quite buy :)
Either some upgrade (not likely to me) or some other user app that may have been taking control over the resolution (thinking of Wine apps and games) and some series of actions reset it.

---

### Post by gnosis2 on 2014-06-22
I'm a complete noob to Linux distributions, so i don't know how to solve my problems and i can't find an answer anywhere i look. So, my problem is I'm using the newest Nvidia driver and my max resolution is 640x480, which it should be 1280x1024. I've used command lines to try to fix this but no progress. Can someone guide me through steps to fix this problem? Using this resolution is dredful. Your help is most appreciated :p

Xrandr:  Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

Hardware specs:
AMD 64 Athlon 2.2 ghz
Nvidia Geforce FX 5200 Graphics card
2GB System RAM

---

### Post by QIII on 2014-06-22
[I]Threads [B]Merged.


[/B][/I]Please do not start multiple threads on the same subject.  It causes confusion and dilutes the community's efforts to help you.

---

### Post by gnosis2 on 2014-06-22
I'm unfamiliar with these forums so i apologize. Though i am tearing my hair out trying to change the resolution in lubuntu. I'm desperate for an answer.

---

### Post by QIII on 2014-06-22
Please be patient.  This is a forum of volunteers from all around the world and all time zones who are here as they have time to be.  Nobody here, including the Staff, is a paid technical support employee of Canonical.

Someone will be along in due time.

---

### Post by brycenesbitt on 2014-06-27
I just installed a fresh LUbuntu 14.04 Guest, under VirtualBox, with a Ubuntu 12.04 Host.
The resolution is stuck at 640x480:

```

# xrandr
xrandr: Failed to get size of gammer for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected
  640x480 73.0*

```
Virtual box additions 4.1.12 are installed.

See also [http://askubuntu.com/questions/452108/cannot-change-screen-size-from-640x480-after-14-04-installation-on-virtualbox-os](http://askubuntu.com/questions/452108/cannot-change-screen-size-from-640x480-after-14-04-installation-on-virtualbox-os)
which is the same issue on Ubuntu itself.

---

### Post by bapoumba on 2014-06-28
I know these are an older threads :
[http://ubuntuforums.org/showthread.php?t=1577614](http://ubuntuforums.org/showthread.php?t=1577614)
[http://ubuntuforums.org/showthread.php?t=2010302](http://ubuntuforums.org/showthread.php?t=2010302)

---

