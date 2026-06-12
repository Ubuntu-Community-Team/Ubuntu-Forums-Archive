---
title: "Ubuntu 12.04 Sound does not work."
date: 2012-08-11
forum: New to Ubuntu
---

### Post by bashhimup on 2012-08-11
Hello. I have a desktop computer with external speakers plugged in. The problem is, the speakers won't work! On ubuntu 10.04 or 11.10 (i think) the speakers worked. Why not now?
Chip: Realtek ALC662 rev1
Please help! :confused:

---

### Post by bashhimup on 2012-08-11
Someone help!!! :(

---

### Post by RedRat on 2012-08-11
> **bashhimup said:**
> Hello. I have a desktop computer with external speakers plugged in. The problem is, the speakers won't work! On ubuntu 10.04 or 11.10 (i think) the speakers worked. Why not now?
Chip: Realtek ALC662 rev1
Please help! :confused:
I can commiserate with you. But I found it to be application specific. I did a virgin install of 12.04 on an HP machine. Found that I could get my mp3 collection to play through Audacity but not through Amorok or Guyadeque. The speakers work when I test them using the sound app, so the OS seems to be speaking to the speakers. However, when I attempt to use Amorok or Guyadeque, I hear only the briefest of a sound than it goes mute.

I have asked this here also and got no response. I suspect that it is something specific to 12.04.

---

### Post by bashhimup on 2012-08-11
It dosen't work in the settings app to when i try to test it.

---

### Post by RedRat on 2012-08-11
> **bashhimup said:**
> It dosen't work in the settings app to when i try to test it.
Have you tried plugging your speakers into the headphone outlet. Or do you have headphones plugged in. In some cases, plugging in the headphone cuts out the speakers. How about headphones? Do they work? Check the volume setting on the upper right side of the panel. Has it defaulted to mute?

---

### Post by mastablasta on 2012-08-11
try to reload the modules. 

sudo alsa reload -c

otherwise it seems there is a bug in kernel (again).

---

### Post by NikTh on 2012-08-11
Hi , 
open a terminal and try this command 
```
echo 'options snd-hda-intel model=auto' | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` 
reboot your computer and see if your problem fixed.
Thanks

---

### Post by bashhimup on 2012-08-11
I WAS STUPID.
Apparently my matrix setting on my speaker was on. I turned it off and now it's fine.
Thanks for helping anyways.

---

