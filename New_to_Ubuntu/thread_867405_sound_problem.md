---
title: "sound problem"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by winsane on 2008-07-22
My sound is working great. I have sound in my video games and my desktop sounds work.  However, when I try to play a music file, I get a box that pops up and says "(noatun or juk or soundserver)The KDE crash handler".  When I click it, it keeps coming back.  It says the name of the program in the first box , then soundserver in the second box.  Did I miss an update or something?

---

### Post by winsane on 2008-07-24
I am using a Sound Blaster Live! card and want to get it working on Ubuntu 8.04.1....

I have installed and when I type lspci -l, I can see it.
Modprobe shows the emu10k1 module.  When I type startx, it loads up the GUI and the first thing on the screen is KDE crash message for soundserver. I don't know what else to try. 


Here is my /etc/modules file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse


       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-emu10k1
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

---

