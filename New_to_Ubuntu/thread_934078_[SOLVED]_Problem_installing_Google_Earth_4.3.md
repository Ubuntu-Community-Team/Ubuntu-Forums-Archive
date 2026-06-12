---
title: "[SOLVED] Problem installing Google Earth 4.3"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by RobHK on 2008-09-30
I installed Google Earth 4.3, When I try to run it I get the Google Earth splash screen for a few seconds then the system crashes and I find myself at the  login screen.

The description in Synaptic says I have to accept a EULA but I wasn't presented with one at any stage. There is also a reference to "Medibuntu", which I didn't understand.

---

### Post by oldos2er on 2008-09-30
Medibuntu is a repository for non-free software. See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 As for your GoogleEarth problem, what video card are you using?

---

### Post by jualin on 2008-09-30
-------------Database error post-----------------

---

### Post by RobHK on 2008-09-30
> **oldos2er said:**
> Medibuntu is a repository for non-free software. See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 As for your GoogleEarth problem, what video card are you using?

NVidia.

I have run Google Earth before on Ubuntu on this machine. Probably an earlier installation or I'd still have it.

I haven't tried installing Google 4.2 instead of 4.3 but I will.

---

### Post by RobHK on 2008-09-30
> **RobHK said:**
> NVidia.

I have run Google Earth before on Ubuntu on this machine. Probably an earlier installation or I'd still have it.

I haven't tried installing Google 4.2 instead of 4.3 but I will.

I must have been mistaken about the EULA, because I reinstalled and got it, but the program still won't run. Same symptoms.

I tried 4.2 as well, but the result was the same.

---

### Post by oldos2er on 2008-09-30
> **RobHK said:**
> I must have been mistaken about the EULA, because I reinstalled and got it, but the program still won't run. Same symptoms.

I tried 4.2 as well, but the result was the same.

 So you've got an Nvidia card, which particular card? Geforce or something else? Please be specific. The error you described can happen if you do not have 3d hardware acceleration enabled.

---

### Post by RobHK on 2008-10-03
> **oldos2er said:**
> So you've got an Nvidia card, which particular card? Geforce or something else? Please be specific. The error you described can happen if you do not have 3d hardware acceleration enabled.

NVIDIA GeForce4 440SE with AGP8X. No idea about the 3d  hardware though.

---

### Post by oldos2er on 2008-10-03
Look under the menus System. Administration, Hardware Drivers, and enable the Nvidia driver from there. Then reboot and check Googleearth again.

---

### Post by RobHK on 2008-10-05
> **oldos2er said:**
> Look under the menus System. Administration, Hardware Drivers, and enable the Nvidia driver from there. Then reboot and check Googleearth again.

Thanks. I've been doing stuff that needed Windows over the weekend so I didn't run Ubuntu, but I'll give it a try and let you know what happens.

---

### Post by RobHK on 2008-10-06
> **oldos2er said:**
> Look under the menus System. Administration, Hardware Drivers, and enable the Nvidia driver from there. Then reboot and check Googleearth again.

Thanks. You were right. :) With earlier installations this got option was offered right at the start, but I seem to recall now that this time there was an issue so it couldn't be done at the start, and since then it never offered itself again.

---

