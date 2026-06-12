---
title: "DVD playing errors"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jasontu on 2008-07-08
I have about 5 different media players installed on my Ubuntu machine, gxine, totem, mplayer, v-something... all but mplayer give me an error whenever I try to run commercial DVD with menues.  Mplayer will play with a bunch of artifacts on the screen and tell me that the buffer is being overloaded for some reason.

Can anyone recommend what I may be doing wrong?

I followed the guide for DVD playback here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and I have run these two line commands:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
and
sudo apt-get install gxine libxine1-ffmpeg

There was some kind of error message on the first but I was able to fix it somehow... or maybe I didn't.  These two commands allowed me to get mPlayer to the point is is now.  I have also run the command to set the DVD to region 1.

Thank you,

Here are my machine specs:
Intel Pentium 4 540
nVidia - EnvyNG drivers Axle nVidia 6600 PCI-e 512 mb
2 GiB of RAM
SATA 3.0 G/sec

---

### Post by bumanie on 2008-07-08
The official repository is third party called [medibuntu]("https://help.ubuntu.com/community/Medibuntu") Follow the guide there. I use vlc player - it plays virtually every codec known. In vlc click on file and then click open disc and it should play. > sudo apt-get install vlcin terminal to obtain vlc player.

---

### Post by jasontu on 2008-07-11
I had tried VLC before to no avail, but I tried again after reading your post and *ding* it worked perfectly.  Clearly you are some kind of magical genie.  Or I did something that fixed it for VLC but not the others and completely forgot what it was I did.

---

