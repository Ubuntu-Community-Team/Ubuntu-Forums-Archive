---
title: "Volume adjustment doesn't work"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-26
Hi,

I just tried the volume taskbar icon to adjust my music volume just to see, that it doesn't have any effect on the computer volume.
I'm on lubuntu 11.04, haven't had any problem in ubuntu with another computer but the same sound system and it worked good. I already did run the additional drivers thing but it didn't find any.

I would really like to be able to adjust the volume, but ubuntu doesn't run on my machine. What could I be doing wrong?

---

### Post by Rodney9 on 2012-02-26
I would use ```
alsamixer
``` in the terminal and check that nothing is muted, see picture below.

Also pavucontrol is helpful for sound control

sudo apt-get install pavucontrol

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by cheatos on 2012-02-26
Well, I've tried running the alsamixer command and it seems like my master volume switch doesn't affect anything. I can turn it all the way up or down, the only thing that changes something is the PCM control and I couldn't figure out how the tutorials you have posted may help me concerning that problem, it seems like these are more for the case that you don't have any sound, my problem is adjusting the sound...
When I use the VLCs built-in volume control it works just fine, as well as with mocp, I don't know what I can do, maybe the system volume control can be adjusted so it regulates the PCM loudness?

---

### Post by cheatos on 2012-02-28
bump

---

### Post by jasiek12 on 2013-02-17
Have the same problem sound controll in youtube works but the usual dont, what to do?

---

### Post by jasiek12 on 2013-02-17
OK i fond it do following

 1  sudo apt-get remove --purge  pavucontrol
 2  sudo apt-get clean
 3  sudo apt-get install pavucontrol
 4  sudo reboot

:guitar:

---

### Post by cheatos on 2013-02-19
So, out of curiosity, don't you use the alsamixer, or is this another package?
Because when I adjust the volume in the alsamixer it works, but with the button on the taskbar it doesn't...

---

