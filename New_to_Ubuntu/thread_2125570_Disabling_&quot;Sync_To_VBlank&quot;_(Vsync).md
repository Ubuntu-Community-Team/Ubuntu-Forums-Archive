---
title: "Disabling &quot;Sync To VBlank&quot; (Vsync)"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by totallynuts on 2013-03-14
Hi folks,
 
i was curious what Linux is all about and so i grabbed a copy of the  latest Ubuntu and installed that on my machine and I am quite impressed  by how easy and nice everything is :>
 
However this means that I'm still quite the newbie, and here's my  problem: I installed ancient Counterstrike (oh my childhood..) and  everything runs perfectly except for the fact that the frames per second  are limited to 60 which should be at 100. I managed to find out that i  need to turn vsync off in Compiz aswell as in the X.org "device",  however i have no clue how to handle X since it is one big black box to  me. I came upon some commands that allow me to edit the Xorg config  file, however apparently the xorg.conf isn't accessible ("server already active for display 0").
And I did try adding 'export vblank_mode=0' to some certain .rc files (somewhere in /etc/) like someone suggested, without success.

I am running Ubunto 12 64-bit on a AMD Phenom with a Radeon 4870 graphics card and the standard Linux drivers (not the proprietary ATI CCC).
 
Thanks a lot for your help.

---

### Post by DuckHook on 2013-03-14
The easiest way to turn off vsync at the driver level is to install the proprietary drivers and then turn off vsync in *catalyst*. If you want to stick with *radeon* instead of *fglrx*, then it appears to be a much more involved process. I can only offer limited direction because I've never tweaked any options using the *radeon* driver, but the man page is [here]("http://manpages.ubuntu.com/manpages/precise/en/man4/radeon.4.html") and refers to setting an option in *KMS*. It doesn't give any examples, and the only way I know to set kernal mode options is at bootup in GRUB. You will have to Google for examples, or wait for one of the gurus to respond as I am out of my depth on something like this.

---

### Post by totallynuts on 2013-03-15
Thanks a lot for the reply. 
Trying to install the Catalyst drivers was the first thing i did after having installed Ubuntu, however that failed miserably. Apparently some package refused to get installed properly and so all i got to see after the next reboot were flashy colors and some yellow gibberish what forced me to reinstall Ubuntu, since all i was left with was a console\terminal in the end (playing around with cd, ls and mkdir did not entertain me too well :rolleyes:). But i got across some super-detailed windows-user-proof tutorial on how to install ati drivers properly, so i'll give it another try :)

adieu

---

### Post by totallynuts on 2013-03-15
Okay, square one again. This time i did the installation via Synaptic Package Manager by just selecting the fglrx driver + ccc package and applying the changes. Now i cant open anything, the ubuntu sidebar doesnt show up and Compiz crashes after every reboot. However i can open a console. Is there a way to get back ? I really dont want to reinstall again :(

---

### Post by DuckHook on 2013-03-15
> **totallynuts said:**
> ...However i can open a console. Is there a way to get back ?

To purge fglrx and reinstall radeon, do:```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
``````
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
``````
 sudo dpkg-reconfigure xserver-xorg
```

---

