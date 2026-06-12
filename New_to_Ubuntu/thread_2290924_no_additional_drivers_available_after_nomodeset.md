---
title: "no additional drivers available after nomodeset"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by xavier-letouche on 2015-08-16
So after deciding to try my first distro i have tried dual booting ubuntu from a usb stick without installing it but had to enter the nomodeset parameter since i had a black screen after the grub and it worked, now when i go to additional drivers it says there are no additional drivers available. is this because i am trying ubuntu without installing?

---

### Post by Bucky Ball on 2015-08-16
Welcome. Apparently the drivers for that card (NVIDIA GeForce GTX 970) are not in the official repositories but are in the xorg-edgers repo. See links or the answers on [this]("http://askubuntu.com/questions/561295/how-to-use-nvidia-gtx-970-gpu") page. 

Be aware that it is a bit pointless installing the repo and the drivers, though, as they will be gone on reboot to 'Try Ubuntu'. At least you know that if/when you do install the drivers are available. :)

---

### Post by deadflowr on 2015-08-16
The nvidia-346 drivers are in the repos, fwiw.(at least for 14.04 and up; don't see them in 12.04)
But I think this may be more related to the restricted repos not being enabled in the try ubuntu session.

Anywho, as stated already, it would be moot as the only way to use those drivers requires a system reboot, and thus all those updates would be lost.

---

### Post by xavier-letouche on 2015-08-17
It found the drivers after booting 15.04 instead of 14.04.3 LTS , everything works fine now thank you for all the help. :D[h=2][/h]

---

### Post by Bucky Ball on 2015-08-17
All good. Please mark as solved (see link in my signature for how) and good luck with it. :)

---

