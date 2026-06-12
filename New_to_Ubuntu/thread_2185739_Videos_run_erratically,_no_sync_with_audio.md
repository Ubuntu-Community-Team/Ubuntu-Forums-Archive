---
title: "Videos run erratically, no sync with audio"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by olli-sylvanne on 2013-11-04
Ubuntu 12.04 LTS with Xfce, ASUS eeePC, Atom 1,33 GHz, 2 GB RAM, Intel GMA500 driver. So many variables to select in SMPlayer + Mplayer2, am confused. HD-videos (AVI, not MOV) run perfectly when no sound (if I select wrong audio output driver like pcm). When I get sound on (ALSA), video repetition rate collapses to maybe 1 frame in 10 sec. The log says

"MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team mplayer: could not connect to socket

 mplayer: No such file or directory

 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined."

What is wrong? What should I do and where?
Thank you in advance for an advise.

---

### Post by uzumakifahim on 2013-11-04
Have you tried with any other player, like VLC?

---

### Post by olli-sylvanne on 2013-11-04
l have installed VLC several times, also on Unity side. Cannot get any video running. Probably crashes.

---

### Post by coffeecat on 2013-11-04
I wonder if the problem is that you are attempting to view HD videos in an under-powered system. Also - you have the Intel GMA500 video device. This is the Poulsbo graphics card which is known to be problematic in Linux. My guess is that the CPU can't keep up with the processing that is required of it.

Have you tried running standard definition videos? Any problems there?

---

### Post by philinux on 2013-11-04
> **olli-sylvanne said:**
> l have installed VLC several times, also on Unity side. Cannot get any video running. Probably crashes.

Try this short clip for comparison. [http://www.hd-trailers.net/movie/ender-s-game/](http://www.hd-trailers.net/movie/ender-s-game/)

It plays a bit erratic in browser using flash but better when downloaded. It plays ok in movie player but great in VLC.

This is on an acer 1410 64 bit, Intel celeron cpu 743 @ 1.3 GHz and integrated intel mobile GM45 express chipset.

---

### Post by olli-sylvanne on 2013-11-04
Thank you for advise.

We'll I'd wish to have for videos the same q level as in WIN7. Otherwise Ubuntu is way faster than W. 

I played the above movie trailer. Was ok in browser and SMPlayer, but no sound. Just played my own videos, sound was this time ok.
I often have HD-video coming nicely, no sound and when I finally get the sound on (many places to try), the video stops, sound runs ok.

---

### Post by philinux on 2013-11-04
> **olli-sylvanne said:**
> Thank you for advise.

We'll I'd wish to have for videos the same q level as in WIN7. Otherwise Ubuntu is way faster than W. 

I played the above movie trailer. Was ok in browser and SMPlayer, but no sound. Just played my own videos, sound was this time ok.
I often have HD-video coming nicely, no sound and when I finally get the sound on (many places to try), the video stops, sound runs ok.

Sounds like video card to blame as coffeecat said. Well that's to say intel's support for it under linux.
[http://en.wikipedia.org/wiki/Poulsbo_%28chipset%29#Poulsbo](http://en.wikipedia.org/wiki/Poulsbo_%28chipset%29#Poulsbo)

---

### Post by olli-sylvanne on 2013-11-05
Hello, thanks for help. I think I know the source of the problem. 

The problem:
- might get all running well, but when you restart computer, video goes in slow steps and sound is cracking or no sound
- time runs at double speed.

The reason is Rhytmbox. I deleted it and now have SMPlayer + Mplayer2 running in Unity in a consistent way. When I shut down and restart, all is like I left it. Minor problem with video-audio sync remains. The sync adjustments at SMPlayer do not help much.
Videos with about 1300*700 .avi run in window in a tolerable way.

My installation: ASUS eeePC 1101ha, Atom processor, 2 GB RAM + Ubuntu 12.04 LTS + Unity.

---

### Post by SeijiSensei on 2013-11-05
> "MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team mplayer: could not connect to socket

mplayer: No such file or directory

Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined."

Mplayer is compiled to look for an infrared remote control device like you would use to connect to a TV.  When it doesn't find one, it logs this harmless error.

As I believe I wrote in your other thread, you'll have problems pushing H.264 HD video through that Intel chip.  Have you watched any DivX/XviD encodes in the AVI container?  I bet they play fine.  

[This site](http://www.auby.no/files/video_tests/) has a bunch of clips in different encodings that you can use for testing.

---

### Post by olli-sylvanne on 2013-11-05
Thank you for the video page. I'll test. What an excellent introduction into the fantastic world of videos. So far I have known nothing of it, except that the contents are packed.
A learning experience, thank you for it.

---

