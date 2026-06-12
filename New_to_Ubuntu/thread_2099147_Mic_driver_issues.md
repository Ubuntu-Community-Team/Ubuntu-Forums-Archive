---
title: "Mic driver issues"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Hannahsaurus on 2012-12-28
Hi, I've been running ubuntu 12.04 for a while now but I've not managed to fix this glitch.

Skype works fine but the sound quality from my mic is poor (although audible) on the other end. I can hear fine my end. 
It's not the hardware as I've tried plugging in an aux headset and no change. 

Is it possible that my mic drivers are slightly wrong? I'm not sure what else to try.

The computer is a Fujitsu Siemens ESPRIMO MOBILE V5515.

Any help would be really great as I'm going abroad next week for a while and I want to be able to keep in touch!

Thanks!

---

### Post by I8NY on 2013-01-03
Well good thing that the mic works already.  Mine didn't work right away in Ubuntu.  Since you tried two mics, if I read your post correctly, then it is probably the driver.  Just in case test to see if the external mic works fine on another PC.  Ubuntu uses pulseaudio which isn't as compatible as ALSA but is better than 11.xx and before.  You can install ALSA and uninstall pulseaudio.  There are many guides online to do that.  Before that, I would test the mic by doing a local recording and playing it back to see if there are issues with the whole mic or if it is just Skype (there is a pulseaudio to ALSA converter that adds static sometimes to Skype calls).  Also check in the ubuntu volume setting to see if the mic is turned down.  I have missed this a couple times and it has caused low mic volumes for me.  The mic should work in the standard ubuntu audio driver.  It is way easier than ALSA to setup.  Try the stuff above before switching drivers and reply if anything works or changes.

---

