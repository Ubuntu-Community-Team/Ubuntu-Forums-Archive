---
title: "Pulseaudio - no sound with flash and clementine?"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sumski on 2011-08-25
Using Kubuntu 11.10 - upgraded from Natty. 
There's no sound playing with ie. youtube videos , or with clementine - in clementine i tried to change output module , but that didn't help, only removing pulseaudio helped. Note that audio was working fine with Amarok (using phonon-vlc). Can anyone reproduce this?

---

### Post by damormino on 2011-08-28
You may want to try this:
[LIST=1]
[*]Open gnome-terminal.
[*]Type: sudo apt-get install -y --fix-broken --fix-missing ia32-libs libasound2
[*]Press Enter.
[/LIST]

---

### Post by sumski on 2011-08-28
thanks for the reply! This was before ia32-libs breakage, and i'm using 64-bit flash, but i will try with libasound2

---

### Post by rajeev1204 on 2011-08-28
Same here bit flash .Sound on youtube is garbled or skips sometimes or goes into an endless loop.The older version of 64 bit alpha worked better for me.Maybe its a flash problem i dont know.

---

### Post by buzzmandt on 2011-08-28
using kubuntu 64 bit, and 64 bit flash, no problems here
couple days ago installed the 64 bit flash when the 32 bit one died (ia32 thing)
you could try reinstalling flash

for 64 bit
```
sudo apt-get install flashplugin64-installer --reinstall
```

for 32 bit
```
sudo apt-get install flashplugin-installer --reinstall
```

---

