---
title: "nVidia driver fails Unbuntu 12.10 64 bit new install"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by RandyN on 2013-03-13
Greetings! ):P 

I'm new to Unbuntu and have been having graphic driver issues.

Rig: Dell Dimension 9200 Duo Core at 2.1 GHz
nVidia GT 240
4GB RAM

The only way I've been able to successfully get to the desktop is to use the 'nomodeset' switch with the noveau (sp?) driver. I have tried numerous guides on installing the nvidia driver and always end up at the same place...a desktop wallpaper with no desktop. I can right click, choose Change Wallpaper then I can choose All Settings to change the driver back to noveau. I tried every incarnation found in the software center and followed a number of guides using Terminal installs without any luck whatsoever.

I am currently re-installing Unbuntu 12.1 to bring me back to a default clean install.

Does anyone have any advice why the nvidia drivers fail to work? Or a guide that actually works for installing nvidia drivers? I would like to install the latest 310 version as the performance of this driver is supposed to be significantly better.

TIA,
Randy

---

### Post by ManamiVixen on 2013-03-13
Upon clean install, the linux headers are broken. So to fix them, in terminal type, "sudo apt-get --purge autoremove" Then do "sudo apt-get install nvidia-current" That will reinstall the headers and properly install the driver. It's best to do this from first boot on clean install or after updating the system. The update will fix the kernel headers as well.

---

### Post by RandyN on 2013-03-13
Thank you, the system is currently being updated so I'll post my results when I've been able to complete the steps suggested.

---

### Post by RandyN on 2013-03-13
Excellent! Thank you very much, ManamiVixen!

After the updates I did the purge and install steps as you said. After a reboot I saw the nVidia screen flash and now my screen resolution is correct for the monitor and things are running smoothly.

I check in Software-Center and it is running the recommended driver, which I will leave as for now. If I want to experiment and try the 310 version I gather I simply enable it in Software-Center and don't have to work in a Terminal window anymore?

---

### Post by ManamiVixen on 2013-03-13
You are welcome. You could do the software center if you like. :) The terminal was just a way for you to post errors here durring install for deeper troubleshooting if things didn't work out. Also, if you like, you can add the xorg edgers ppa which would give you driver 313.26 of Nvidia. :) But the ppa could be unstable. So be weary.

[FONT=arial black]
If you are brave to try it and don't mind getting dirty if needed:[/FONT]
[B]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get remove --purge nvidia-current
sudo apt-get install nvidia-313

[/B]

---

### Post by ManamiVixen on 2013-03-13
Also, it might be a good idea to sudo apt-get dist-upgrade before doing sudo apt-get install nvidia-313

---

### Post by RandyN on 2013-03-14
In for a penny in for a pound. :P I'll give it a shot but first the upset face what's the symbol there a dash?
sudo add-apt-repository ppaorg-edgers/ppa ---Hmmm I copied and pasted the line and think I have my answer!

In case I need to revert back:
sudo apt-get --purge autoremove
sudo apt-get install nvidia-current

That should do the trick?

Thanks again,
Randy

---

### Post by ManamiVixen on 2013-03-14
Yes. That is correct. :)

---

### Post by RandyN on 2013-03-15
sudo add-apt-repository ppa:mad:org-edgers/ppa 
this was a test, right? ;) I ended up googling this for the correct syntax: the mad face is actually a colon **:** but the wysiwyg editor keeps messing with that


I made the mistake of not restarting the pc (probably a good idea after such a major change up) before launching into alien arena (my way of benchmarking) so the system ended up crashing. After a restart though I was able to launch the game and my FPS shot from 20-30 to a solid 60. Very nice. I only checked out the one map and noticed there was a couple of graphic anomalies...where "fireflies" were just squares and players had a square attached to their butt. 

I didn't even know that ver 3.13 was available so the question now is...what's the best way to "update"? With Launchpad now added to my repository list will new driver updates automatically show up in the 'additional drivers' tab or would I have to do a sudo apt-get update?


]Thanks again for the advice...the learning curve is becoming less steep every day. :D

---

### Post by ManamiVixen on 2013-03-15
Once you add a PPA, it will automatically update with the rest of the system and install whatever updates it has. So no need to do anything, except update like normal. :)

---

### Post by RandyN on 2013-03-15
A tip of my hat to you! Thank you so much for the wonderful advice and help.

---

