---
title: "Right hand (only) sound channel still crackles."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by wetinwales on 2008-09-30
Hi. Running Ubuntu 8.04 on a laptop circa 2002. AC97 sound card.
Crackle from right hand channel. OK in Windows (dual boot)

Last night it solved by changing type in Sound Prefs. 
Then worked OK in most types.
Re booted tonight and its back to normal - crackling !

Could this be sampling rate? Should sampling rate be 44100 or 48000?
In which file do I change default to 48000?

Ta!
Wetinwales:

---

### Post by markbuntu on 2008-09-30
No, that should not generally be the problem but with certain via chipsets it may be with the AC'97. Due to the amount of tweaking that OEMs did to that chip, there are many "quirks" that the driver must be set for.

First, we need to find our which driver is being use, in a terminal type:

cat /proc/asound/modules

If it says

snd_atiixp which is very common for chips of that era, edit the /etc/modprode.d/alsa-base file and add this line to the end:

options snd_atiixp ac97_quirk

If it says snd_intel8x0, add this line:

options snd_intel8x0 ac97_quirk

If it says snd_via82xx, add this line:

options snd_via82xx ac97_quirk

There is more on the AC'97 and its options here, which is a file on your computer. you should expecially read it if you have a via chipset:

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

---

