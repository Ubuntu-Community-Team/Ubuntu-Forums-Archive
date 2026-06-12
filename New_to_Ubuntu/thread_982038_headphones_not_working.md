---
title: "headphones not working"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Morkhaar on 2008-11-14
Hello,
I have no sound coming out of the headphones, when plugged in the speakers carry on playing. 

I have no Switches Tab in Volume Control -> Preferences, just Master, PCM, Digital, and no External Amplifier choice 
All is clicked to unmute but still no result. 

[I]aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/I]

probably something going there but I don't know how to select my soundcard for Alsa...

also 
~$ bash: /etc/modprobe.d/alsa-base: Permission denied
~$ sudo /etc/modprobe.d/alsa-base
sudo: /etc/modprobe.d/alsa-base: command not found

I ve also tried ~$ sudo apt-get install linux-backports-modules-hardy, not sure though what exactly I was trying to do :)

I m using Hardy on a Sony Vaio VGN-FZ31E,my sound card is SigmaTel STAC9872AK (I think)

---

### Post by jbrown96 on 2008-11-14
check the channels with ```
alsamixer
``` I don't know why it won't mute your speakers though.

---

