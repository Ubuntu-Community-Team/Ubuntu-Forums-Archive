---
title: "Drivers?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by AilesGrises on 2008-05-16
where can I download Ubuntu drivers for my wifi card etc.? The wifi acts a little weird and so does the mouse.

Also, youtube isn't working and I'd like to get it working >.< I have no idea how, and I need it explained in the most basic terms possible >.>

Another thing is, how do I update?

And, is Ubuntu normally less efficient than windows? My professional windows XP worked fine with firefox azureus and winamp running, but Ubuntu can't handle music box and bittorrent (It freezes)

(I guess I should've revised the title to indicate I was asking a bunch of questions >.<)

---

### Post by kesman on 2008-05-16
For flash, search for flash plugin in synaptic package manager and install it. For your wlan, look in system->administration->hardware drivers.

---

### Post by AilesGrises on 2008-05-16
"Starting without administrative privelages

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them"
That's what is said when I tried to apply patches from synaptic.

How do I fix it so I have administrative abilities for everything? I'm the only one using this comp.

---

### Post by kesman on 2008-05-16
It should ask for your password when you open synaptic. Are you by the way running the LiveCD or is the system fully installed?

---

### Post by adult swim on 2008-05-16
first go to the synaptic pacakge mangager system/administration/synaptic package manager and then click on settings/repositories.  make sure that the first four boxes are checked and then click close.  opne up a terminal, applications/accessories/terminal and type in ```
sudo apt-get update
``` to get the flash working go to a terminal and type in ```
sudo apt-get install flashplugin-nonfree
```
as far as ubuntu crashing with bt and music playing, you have a problem there.  im not sure what is going on with that but i bet there are people that can help.

---

