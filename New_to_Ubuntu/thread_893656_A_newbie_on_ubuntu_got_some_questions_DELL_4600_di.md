---
title: "A newbie on ubuntu got some questions DELL 4600 dimension ..."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by hitman1985 on 2008-08-18
hi there,

i just installed ubuntu 8.04 hardy on my dell dimension 4600, everything seemed to be fine untill.

i cant have multiple audio streams runing i guess, ie - i want to call someone over skype it says problem with audio device, pidgin runs and throws its sounds around ok, but if i watch a movie i cant hear the sound of my regular mp3 rhytm player.... someone has to be wrong with the sound i guess. 

also the sourrund card wont give out surround it ll only play stereo :( 

heres a little cut out of my pci device list :

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


and the whole system looks like this:

intel p4 2800 mhz socket 478 
2048 mb crucial ddr ram 
dell dimension 4600 motherboard with onboard everything (execpt video)
agp 5200 FX 128 mb (runs fine, just a little choppy on the compiz and video replays)
160 gb sata hdd (maxtor) with a single ubuntu partition (no more microsoft products wanted! ever again)

and all over i got to admit ubuntu has done a very good job so far, for me as newbie it was easy to solve problems like flashplayer and java. but the problems up top is what i m fighting with right now atm.

thanks in advance

---

### Post by jbrown96 on 2008-08-18
Try using/not using Pulseaudio. System-->Preferences(or administration?)-->Sound and change the playback device. You can try several. Pulseaudio is supposed to fix problems like this, but it's buggy. The preferred playback devices are pulseaudio, alsa, oss... So try those first.

---

### Post by mikewhatever on 2008-08-18
Yeap, I had to change everything to alsa and it started working as well as in previous versions.

---

### Post by hitman1985 on 2008-08-18
i wrote another thread with more details on it in here, sorry for the double post :(

but if i change everything to alsa (skype then to default) i dont get no sound at all from skype

---

