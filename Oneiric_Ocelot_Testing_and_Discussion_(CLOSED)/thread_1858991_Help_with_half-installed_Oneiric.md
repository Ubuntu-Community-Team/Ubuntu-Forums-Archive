---
title: "Help with half-installed Oneiric"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Conzeit on 2011-10-13
Ok, Linux newb here,  I was updatiing from Natty to the new Oneiric today at like 3 am, I had already downloaded all the packages and I was in the middle of installing them but then my laptop reset (I just disconnected it from the energy, it had plenty of battery should've kept working) 

So now when I boot it tries to start ubuntu, from what I see loads most of the stuff but it doesnt give me a gui at the end, just a sort of terminal.

tells me my last login, welcomes me to ubuntu and says

679 packages can be updated
0 updates are security

I suspect those packages are the ones  I had downloaded and was in the middle of installing? I suppose the easiest thing now  to recovery my ubuntu install would be just to install those packages, but if you think there's a faster easier way please do tell me

---

### Post by collisionystm on 2011-10-13
faster to reinstall?

---

### Post by Conzeit on 2011-10-13
IDK, I'd have to readownload Oneiric, also would I lose the System I was updating from tho? I dont want to lose my apps and configuration

---

### Post by paul_in_london on 2011-10-13
See if you can boot into recovery mode - you might need to hold down the escape key for a few seconds after the BIOS loads to get the GRUB (bootloader) menu. Choose kernel blah blah (recovery mode). For your latest kernel it should be the 2nd GRUB menu entry.

It should boot into another recovery menu. Choose netroot (root with networking) and try and run these two commands:

```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by Conzeit on 2011-10-13
Oooooh thank you thank you thank you both so much for the prompt reply, I have gotten to terminal by pushing Ctrl+alt+supr then entering my username and password, I'm confident this will work out =)

---

### Post by paul_in_london on 2011-10-13
Good luck! Just be careful if the 2nd command wants to remove anything. If you see {u} after a package it says it's going to remove that should be ok. If you're not sure post what the command wants to do first.

---

