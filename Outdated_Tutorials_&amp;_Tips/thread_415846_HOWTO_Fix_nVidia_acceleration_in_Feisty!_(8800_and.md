---
title: "HOWTO: Fix nVidia acceleration in Feisty! (8800 and legacy users look here)"
date: 2007-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by etherealremnant on 2007-04-20
Okay so the restricted drivers manager has made things a mess for a lot of people with newer and older nVidia cards.

I, myself, have an 8800GTS card and I was getting really upset about the fact that I could get my card to work once after installing the nvidia driver and then after I rebooted, I'd have to install it again.

So here's the solution, originally taken from: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Basically, the restricted modules are getting load priority over the nvidia-installed module.

First off, sudo apt-get install build-essential (or install build-essential through Synaptic or aptitude)
Then sudo apt-get install xserver-xorg-dev
Now sudo nano /etc/default/linux-restricted-modules* and change the DISABLED_MODULES="" to DISABLED_MODULES="nv"
Ctrl-O to save
Now reboot.

Upon reboot, download the proper driver package from the nVidia website and save it somewhere where you can easily access it.
Hit Ctrl-Alt-F2 to open up a console and login.
Type sudo /etc/init.d/gdm stop to shut down Xorg
Now run sudo sh NV* from the location where you saved the nV file.

Run through the installer and tell it to update your xorg.conf for you.
Reboot once again (just type reboot at the console) and you should have full nVidia acceleration!

---

### Post by bluehue on 2007-04-21
Correct me if I'm wrong, but it seems like the Feisty instructions are essentially the same as for Edgy: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) (see installation method 2)

Edit: Followed the Edgy instructions and the restricted drivers (nvidia 9755) were detected (gave me a pop-up dialog) as soon as I restarted gnome. I edited my xorg.conf file to include the 1600x1200 resolution and I can now run my LCD at native resolution :)

---

### Post by MontyV on 2007-04-22
> **etherealremnant said:**
> 

Now run sudo sh NV* from the location where you saved the nV file.

Run through the installer and tell it to update your xorg.conf for you.
Reboot once again (just type reboot at the console) and you should have full nVidia acceleration!

I've never used console mode before so if I saved my newly downloaded nVidia driver here "/data/drivers/nVidia" what do I type?  sudu sh NV*.....?  Also how do i get back or restart?

---

### Post by Dr_Deadmeat on 2007-04-22
Then you use the following:
```
sudo sh /data/drivers/nVidia/NV*
```
If you placed it in your home folder under data/drivers/nVidia you have to use this one:
```
sudo sh ~/data/drivers/nVidia/NV*
```
Hope this helps =)

---

### Post by camaroace on 2007-04-25
This fix works I found it on the authors website [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

Hope this post helps other people.

---

### Post by Mizled on 2007-04-25
Thanks! Worked like a charm. I was getting very frustrated when Restricted driver wasn't working and Envy wasn't working either. Cheers!

---

### Post by MontyV on 2007-04-25
> **etherealremnant said:**
> 
Run through the installer and tell it to update your xorg.conf for you.
Reboot once again (just type reboot at the console) and you should have full nVidia acceleration!

This is probably a stupid question but I swear I've been searching on how to switch to root in console with no luck.  The steps seem to work well and it installed everything like you said.  Just with the last part where you say to type "reboot" it is saying "reboot:  Need to be root" 

How do i switch to root so that i can reboot?

EDIT:  Scratch that "sudo reboot" worked.

---

### Post by MontyV on 2007-04-25
Should I be seeing this message:

"In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported.

Because the software is proprietary, it cannot easily be changed to fix any future problems"

---

### Post by petersjm on 2007-04-26
> **etherealremnant said:**
> Reboot once again (just type reboot at the console) and you should have full nVidia acceleration!

Dangit! You learn something new every day! For months when rebooting from console mode, I'd type "sudo shutdown -r 0" (meaning shutdown, and "-r" reboot, in "0" seconds (ie. now)"... "sudo reboot"--how come I never thought of that?! LOL

---

### Post by camaroace on 2007-04-26
> **MontyV said:**
> Should I be seeing this message:

"In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported.

Because the software is proprietary, it cannot easily be changed to fix any future problems"

Hmmm....I don't get this message but did you enable the NVIDIA xorg config?

```
sudo nvidia-xconfig
```

---

### Post by MontyV on 2007-04-28
> **camaroace said:**
> Hmmm....I don't get this message but did you enable the NVIDIA xorg config?

```
sudo nvidia-xconfig
```

I did not see those instructions.  Well I did it and nothing so far so we'll see what happens I guess.  The pop us is not there but in the Restricted Drivers Manager that comment is still in there.

---

### Post by tbeehler on 2007-06-02
worked for me in kubuntu.  thanks!

---

