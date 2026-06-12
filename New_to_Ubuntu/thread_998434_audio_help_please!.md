---
title: "audio help please!"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by adamgram on 2008-11-30
I set up my computer (Dell Dimension E521) with Ubuntu 8.10 last weekend, but I've been having a lot of trouble getting the sound to work on it.  The sound works fine in windows.  After trying a lot of different things, I found the right driver for my sound card (Creative SB X-Fi), but it only works in 8.10.  I tried it in 8.04 and clicking on the volume thing at the top of the screen gave an error.  In 8.10 there is no error, but I'm still having trouble with the sound.

At first, the startup sound played, but no file formats were recognized.  I could get sound off the internet as well, opening right in firefox, but couldn't play wavs or mp3s or midi or anything like that.  Today I installed a bunch of other crap hoping to fix it... restricted drivers, KPlayer, and MPlayer, and I tried using Xine but the extra plugins wouldn't install on my computer for some reason.  Now nothing works.  I know that sounds kind of vauge but I was wondering if someone could help me out, point me in the direction of where to look, or give any other assistance.  Maybe there's a package I need to install or one I did install but shouldn't have... I don't really know where to begin looking, but I'm really frustrated with this and would really appreciate the help, thanks!

---

### Post by adamgram on 2008-11-30
okay, the situation has gone from bad to worse here... I started following the advice found here 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
so I did
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and then
sudo apt-get install linux-sound-base alsa-base alsa-utils
and then I rebooted... now it reboots to a command prompt!  no gui of any sort, it's like ubuntu isn't there any more!

---

### Post by markbuntu on 2008-11-30
What you did removes gdm and ubuntu-desktop along with the alsa stuff if you are using gnome.

sudo apt-get install gdm ubuntu-desktop

then reboot

After that, go here:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by adamgram on 2008-11-30
Thanks for your help man!  I got the GUI back, followed all the instructions on the link, but I still have no sound.  After making the changes I made today, I have less than I did when I started... it seems like that link should fix the problem I was having but now I'm afraid I created a new problem while trying to fix something (for like the 10,000th time since installing ubuntu in the first place...).  I might need to reinstall and follow that link again.  Thanks for your help.

---

### Post by markbuntu on 2008-12-01
I have another guide with more extensive sound troubleshooting here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

