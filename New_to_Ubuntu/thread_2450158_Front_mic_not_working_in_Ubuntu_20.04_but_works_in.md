---
title: "Front mic not working in Ubuntu 20.04 but works in windows"
date: 2020-09-08
forum: New to Ubuntu
---

### Post by malyadeep on 2020-09-08
Hi!

I am new to Ubuntu and am currently running Ubuntu 20.04 LTS.  The front panel mic of my CPU does not work in Ubuntu but works well in  windows. I have tried many things like changing the pulseaudio profiles  and the hdajackretask (Though not sure about this whether I did it  right or not) but nothing worked. The rear panel mic seems to work  correctly. I have attached the pulseaudio input panel screenshot and hdajackretask screenshot.

Any help would be great. I am in urgent need of this one.
Thanks in advance! :D:D

---

### Post by malyadeep on 2020-09-10
Hi!

Fortunately I was able to sort out my problem using the hdajackretask  just now. All I did was overrode the front pink mic port with internal  mic and the front green headphone port by line out. After that I chose  the pulseaudio profile analog surround 4.0 + analog stereo input and  everything works fine now.

 I am attaching the screenshot for the hdajackretask configuration and pulseaudio profile settings for reference.

---

