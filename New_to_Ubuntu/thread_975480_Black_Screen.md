---
title: "Black Screen"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-11-08
I really am a total newbie. I have a Compaq Presario sr1619 which I'm doing some upgrades to. I have it set up as a dual boot with XP and Ubuntu 8.10. It had onboard graphics and didn't play well with Compiz, so today I bought and fitted an Nvidia Geoforce 9500GT Super graphics card.

XP is fine because it comes with disk full of drivers, but now when I boot into Ubuntu, all I get is a black screen, not even a prompt of any kind. I do see the usual black and orange splash screen, then a box asking me about configuration files, creating one or using a backup one. This is the poiint where I get lost. Can anyone please advise me?

---

### Post by taurus on 2008-11-08
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Once it's rebooted and you are able to log in again, look in System -> Administration -> Hardware Drivers to see if your nVidia card is on the list.  Click it to install a driver for it.  Don't forget to go into the BIOS to turn off the onboard graphic card controller first before you boot into the recovery mode from GRUB menu.

---

### Post by Cuttysark on 2008-11-08
I tried what you said, and I am getting a bit further, now past the splash screen, and on to where I can see my wallpaper (but no top and bottom toolbars), and then it just hangs, and as there's no reset button on my machine, all I can do is switch the power off then back on again.

---

### Post by phidia on 2008-11-08
In recovery mode try > xfix and report back on that.

---

### Post by Cuttysark on 2008-11-08
I tried that but it didn't help either, however, when I was in XP, I went and took another look at Nvidia's site and found that they did a Linux driver so I downloaded it onto a thumbdrive. I then rebooted using a Hardy live cd and did gksudo nautilus, which let me copy the file into my home folder. I then rebooted again, back to safe mode in Intrepid and got a prompt up, changed directories to the home folder and did the an sh command to the file, and it installed, and when I continued the boot, I got to my desktop.

I then went to System/Administration/Hardware Drivers, and it showed the Nvidia driver, although it also said there was a newer version available but so far I don't seem to be able to download and install it. I'll have another try tomorrow. For now though, I'm already seeing the benefits of my new card over the onboard graphics. Thanks for the advice though, it definitely helped.

---

