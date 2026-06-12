---
title: "[SOLVED] Sound card settings change each startup"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by garyed on 2008-04-24
I've been finally running some audio programs which was my original intention of using Ubuntu. My only problem is every time I boot up I never know what my  sound cards place will be given, 0,1, or 2. I have three sound devices.
1 - Onboard - disabled in bios but still shows up in Gusty
2 - M-audio 2496
3 - Sound Blaster Live  

I mainly use just the M-audio but sometimes I might want some sound out of the SBlive. Anyways everytime I boot up I have to check "/proc/asound/cards"
to find the number of each card to set up Jack for recording. Is there any way to keep the card numbers constant on every boot?

---

### Post by garyed on 2008-04-26
I found this solution in another forum so I figured I'd post it here & in the Multimedia forum.

To solve multiple sound cards order from changing on boot-up take the output  of:

cat /proc/asound/modules
(Should look something like this)
 0 snd_ice1712
 1 snd_emu10k1
 2 snd_via82xx
--------------------
Then edit "/etc/modprobe.d/alsa-base" file & add the following lines to the end of the file in the order you want the cards to be using the results of your output like this:

options snd-ice1712 index=0
options snd-emu10k1 index=1
options snd-via82xx index=2
-----------------------------------
Note: The spacing has to be exact with special notice to no spaces between "=" sign.

---

### Post by ghost_ryder35 on 2008-04-26
congrats!!!! make sure to mark the thread as solved

---

