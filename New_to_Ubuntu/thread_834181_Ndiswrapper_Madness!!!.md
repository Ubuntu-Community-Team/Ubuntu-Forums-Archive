---
title: "Ndiswrapper Madness!!!"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by holasoyneto on 2008-06-19
Hey, yesterday i was very hapy, i made my broadcom card work with ndiswrapper, i browsed all day long, then, i had to reboot, when i rebooted, there was no wi-fi, the wifi led is green, it detects networks, but when i attempt to get online it gets stuck on configuring device 28%.

this is the tutorial i followed [http://geowworld.blogspot.com/2008/03/ndiswrapper-solucion-final-hardy-y.htm](http://geowworld.blogspot.com/2008/03/ndiswrapper-solucion-final-hardy-y.htm)

hope you can help me =D

sorry for my weak english

---

### Post by Corrupt3d on 2008-06-19
Your link is broken, I think this is the correct one:
[URL="http://geowworld.blogspot.com/2008/03/ndiswrapper-solucion-final-hardy-y.html"]http://geowworld.blogspot.com/2008/03/ndiswrapper-solucion-final-hardy-y.html
[/URL]
Have you tried modprobing it?

$ sudo modprobe ndiswrapper -r #disable module
$ sudo modprobe ndiswrapper #reload module

---

### Post by holasoyneto on 2008-06-19
:confused: arghh now it wont detect wireless!?!!?! .__.
¿is there someway i can install kernel 2.4?
my wireless worked fine with 7.10 on kernel 2.4

---

### Post by holasoyneto on 2008-06-19
hmmm it wont help, already tried it
thank you

---

