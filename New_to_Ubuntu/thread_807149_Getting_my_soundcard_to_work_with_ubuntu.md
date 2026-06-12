---
title: "Getting my soundcard to work with ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Qwaz_Dan on 2008-05-25
Just installed Ubuntu this afternoon, and it detected my video card and I've got the drivers for it, which now mean my screen isn't off centre.

I am having problems with trying to get ubuntu to use my soundcard, instead of the sound on my motherboard.

My soundcard is a Creative sound blaster audigy 2 ZS.

i was wondering where i can get the driver/tell ubuntu to use this soundcard.

Thanks

Dan

---

### Post by markbuntu on 2008-05-25
There is a tiny little utility for alsa you can find with synaptic that will let you choose your default sound card. 

alsaconf-gtk. 

You will find it in System/Preferences after you install it and all it does is give you a tiny window which has your sound cards listed. Choose the one you want and exit. 

Then you can go into System/Preferences/Sound and change all the settings from automatic to ALSA and everything will work.

It is by far the easiest way to fix this sort of problem, at least it was for me.

---

