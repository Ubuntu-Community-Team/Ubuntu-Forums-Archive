---
title: "which sound card drivers"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-06
How can i tell which sound card drivers are in use on my toshiba satellite U300-15P laptop?

---

### Post by bumanie on 2008-11-06
the commands > lspci or > lshw should provide that information in a list (which will be quite long).

---

### Post by corkscrew on 2008-11-06
ok the result of lshw for multemedia section is this
[   *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel]
so where do i see the alsa info?

---

### Post by corkscrew on 2008-11-06
ok the result of lshw for multemedia section is this
[   *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel]
so where do i see the alsa info?

---

### Post by handydan918 on 2008-11-06
From your output:

configuration: driver=HDA Intel latency=0 module=snd_hda_intel]

you might try lsmod also. 

Not sure what "alsa" info you are looking for.

---

### Post by corkscrew on 2008-11-06
I'm trying to troubleshoot a very low record level when using external mike with skype. Thought i'd start with the basics and check which driver was being used.
All other sound works fine when playing music or dvd's.
when i plug the mike in and leave the headphone jack unplugged i can speak into the mike and hear the soundout put on the laptop speakers perfectly. Its like a whisper when i use it with skype

---

