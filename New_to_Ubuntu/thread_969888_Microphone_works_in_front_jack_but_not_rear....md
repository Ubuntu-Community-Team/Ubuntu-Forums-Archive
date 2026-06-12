---
title: "Microphone works in front jack but not rear...?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Virtualboxbuntu on 2008-11-03
My microphone seems to work fine when plugged into my front microphone jack, but does not generate any sort of signal when plugged into the back. What's up with this? I'm dual-booting with Vista and the last time I booted into Vista (a long time ago) the microphone worked in both jacks.

I am using:

Linux Mint 5 (based on Ubuntu Hardy)
NVidia card (AFAIK)
Proprietary NVidia driver for graphics card (through EnvyNG)

I don't know if the graphics card driver has anything to do with this, but I don't know, so I'm posting it anyway.

---

### Post by pyromanic123boom on 2008-11-03
No, it's not a graphics card issue. go into a terminal, type 

alsamixer

for the sound mixer.  Then go with the left and right arrow keys and find the font mic or back mic.  As a second option, double click your volume icon in your toolbar, and find it there.

---

### Post by Virtualboxbuntu on 2008-11-05
> **pyromanic123boom said:**
> No, it's not a graphics card issue. go into a terminal, type 

alsamixer

for the sound mixer.  Then go with the left and right arrow keys and find the font mic or back mic.  As a second option, double click your volume icon in your toolbar, and find it there.

Hmm... it works now, but it's extremely quiet, to the point where it's impossible to understand when I speak into it. What's up with that?

---

