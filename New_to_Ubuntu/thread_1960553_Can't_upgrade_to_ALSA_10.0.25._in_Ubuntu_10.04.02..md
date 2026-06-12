---
title: "Can't upgrade to ALSA 10.0.25. in Ubuntu 10.04.02./ IDT 92HD89 chipset / No sound fro"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by eganherman on 2012-04-17
With the current Alsa driver I manage to get sound from the front pannel only ( headphones). 
I do not not 'see' the backpannel : Loudspeakers & the SPDIF outputs.

I modified  options "snd-hda-intel model=MODEL". With several models  ( 3jack, 6jack, ref, hp... , etc) without succces. 
I always get sound only from the front headphone connector. The Alsa driver detects a 76C7 HW instead of mine.

I'm  trying now to upgrade to the latest Alsa driver 10.0.25 as may be I get more from this latest driver :

I compiled and installed as per the procedure described in :

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

After some tweaks ( missing modules , etc, etc).  Compilation & install of  driver, lib & utils  seems OK.

Here is where I beleive I'm stuck :

modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
I have the following  warnings  :
egan@egan-linux:/usr/src/alsa$ sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

When I check what is driver installed,  I still have Alsa 10.0.23. After reboot I still have Alsa 10.0.23.
I don't know what I miss to finish up the installation in Ubuntu and set up the driver at boot time.
My configuration is :
HW : HP  H8-1102 with  I5 2320 core  + NVIDIA GEFORCE GTX 550 Ti + IDT 92H89E  ( Intel HDA).
SW : Ubuntu 10.04.02  Kernel version 2.6.32 40 + lastest version of  NVIDIA driver 295.40 compiled  with Ubuntu + Alsa driver : 10.0.23

Thanks for helping.

---

### Post by nokimey on 2012-05-29
Sorry bad idea....

---

