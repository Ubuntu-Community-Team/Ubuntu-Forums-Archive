---
title: "[SOLVED] No sound on Hardy after upgrade from Gutsy"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Rincewindthewizzard on 2008-06-22
Hello

I just did a version upgrade from Gutsy 7.10 to Hardy 8.04 and I have no sound anywhere. I tried searching the forums for a solution but it got too confusing and I didn't really get anywhere. I am a new linux user and don't know much, so I really need some help. 

I'm using the 2.6.24-19-generic kernel
my motherboard is MSI P965 Platinum and I'm using the KDE desktop

Thanks

---

### Post by Biggy on 2008-06-22
from synaptic package manager install Alsa

---

### Post by Rincewindthewizzard on 2008-06-22
I already have alsa-base alsa-oss and alsa-utils installed. Did a reinstall on all of them but didn't help

---

### Post by Biggy on 2008-06-22
System >preferences >sound >devices

---

### Post by Rincewindthewizzard on 2008-06-22
Umm it seems that my k menu is a bit different, I don't have system - preferences anywhere.. KInfoCenter has a sound tab and it says there that 

Installed drivers: 
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfe7f8000 irq 23

Audio Devices:
0: ALC883 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC883

---

### Post by Rincewindthewizzard on 2008-06-22
Oh well now I really feel like an idiot. Got sound working. After the version upgrade KMix had switched to headphones on the switches tab and after I put the switch back to IEC958 sound was back. 

I'm very sorry for putting you through this trouble when all the time it was about something as simple as that, it just never occurred to me to check the KMix switches tab.

---

