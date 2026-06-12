---
title: "volume via keyboard"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by teranex on 2008-11-23
Hi,

I have a Logitech iTouch keyboard, with volume and a mute buttons. When i press those buttons a semi-transparent window appears, which indicates the volume and whether or not sounds are muted. However, this does not have any effect on the sound. I think this might be the same problem that i had with the volume widget in the gnome panel, at first that also didn't work. I fixed that by changing the 'device and track control' from 'VIA 8235 (Alsa mixer) - Master, to 'VIA 8235 (Alsa mixer) - PCM.
So i guess i will have to do the same for the keyboard-keys, but i have no idea where i can change that...

thx for any help!

---

### Post by beno1990 on 2008-11-23
Go to System -> Preferences -> Sound

And then change the "Default Mixer Tracks" device to the same device you set the volume widget to on the Gnone panel, and then log out and log in again.

---

