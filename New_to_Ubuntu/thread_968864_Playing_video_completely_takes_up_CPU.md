---
title: "Playing video completely takes up CPU"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by holdie on 2008-11-03
I just upgraded to Intrepid Ibex and I'm having difficulty playing videos...basically, everything is running normally with low CPU usage, but as soon as I start playing a video (whether it be with totem,vlc, etc.) the CPU jumps up to 99% and everything becomes unbearably choppy

I'm running the ATI proprietary driver installed through ubuntu

Does anyone have any ideas?  This wasn't a problem with Hardy

---

### Post by jbrown96 on 2008-11-03
Could you give us some info on your hardware (CPU), the codecs being used (I believe that vlc has a dialog for codec info), and the resolution info (if you right click on the video in Nautilus and go to properties, there is a tab for audio/video)? Also for vlc, try changing the playback device; if you are using >=0.9.0, in preferences in general there is a drop-down menu (it says default unless you've changed it). I have had a lot of luck with xvideo and x11.

---

### Post by holdie on 2008-11-04
Sure, I'm' using a Dell Inspiron 6000 with a 1.86Ghz Pentium M processor and 1.2 GB of RAM

Resolution for the video is only 576x432 (and this problem occurs virtually nay time any video is played fullscreen or larger than normal, including with youtube and such)

It looks like I'm using the x264 video codec with VLC (Although again, this happens with any movie program I'm using

---

### Post by holdie on 2008-11-05
bump

---

### Post by LowSky on 2008-11-05
did you reinstalll the proprietary ATI driver when you Upgraded? the open source one will upgrade just fine but the Proprietary needs to be recompiled with each Kernel upgrade.

---

### Post by holdie on 2008-11-06
Yeah, I used the ubuntu restricted hardware program to get the new ati driver...and also this problem occurs regardless of the program, even firefox slows it down

---

### Post by holdie on 2008-11-07
aaaand a bump

---

