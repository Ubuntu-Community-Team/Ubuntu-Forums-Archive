---
title: "AC'97 driver"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by marlan on 2008-08-08
I am trying to get the sound working on my new (second hand) machine, it does work but the volume is extremely low, does anyone know where I can get a Linux driver for the onboard AC'97 sound card. All I can get from Realtek is a list of drivers for that other well known O/S that I am trying everything to avoid.:cool:

---

### Post by fiddledd on 2008-08-08
Never tried xubuntu, but [this](http://www.linuxforums.org/forum/ubuntu-help/114905-low-volume.html) may help.

---

### Post by kpkeerthi on 2008-08-08
The driver is in-built (as a kernel module) in Ubuntu. There is no need to install offline.

To adjust the volume, open a terminal and type
```
alsamixer
```
and make sure the volume levels of 'master' and 'pcm' are as required.

See alsamixer [controls]("http://en.wikipedia.org/wiki/Alsamixer#General_Controls") for some help with the tool.

---

### Post by marlan on 2008-08-08
Thank you KPKeerthi, Eureka, I found it and it is now working. I wonder just how many other goodies are lurking in here. An overall manual of Ubuntu would be a godsend.:biggrin:

---

