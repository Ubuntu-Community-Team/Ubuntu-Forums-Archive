---
title: "[SOLVED] Getting NVidia Working"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by TheUbGuy on 2008-09-06
I have been a long-time OpenSuse user. I had wanted to try Ubuntu for a while - I know a lot of folks using it and it is even used by a good amount of users at work. However, no matter what I tried, I could not get the NVidia driver working. I would enable the driver in Hardware Drivers, and upon reboot I would get the dreaded low-resolution screen with 'can not detect your screen etc'. I tried fresh installs and used Envy - no dice.

I couldn't understand this - since OpenSuse worked with the Nvidia driver flawlessly. I was going to give up, but decided to try this. I saved the xorg.conf from my OpenSuse installation. I installed Ubuntu, switched to the hardware driver. Before rebooting, I edited the xorg.conf file, replacing the driver, monitor, and screen settings with the ones from my OpenSuse installation. Rebooted and *voila* - full 3D and settings. I have Compiz and emerald installed and in use.

If you are coming from another distribution (like OpenSuse) where you have the Nvidia driver working, do what I did and save some heartache - save the xorg.conf file and use those settings once you enable the Nvidia driver - it will save you a lot of headaches!

---

### Post by diablo75 on 2008-09-06
From the sounds of it, the driver probably worked, but it failed to detect your monitor correctly and defaulted to a safe resolution.

If I were you, I would try to use the included restricted drivers manager to enable the nvidia drivers, and then after restart, run:

sudo dpkg-reconfigure xserver-xorg

Follow the on screen prompts (tell it "no" to the question about using the kernel buffer... just my own preference) and then restart the computer when you're done.  You should have more screen resolutions available.

In addition to this, you will likely want to install the nvidia-settings package with:

sudo apt-get install nvidia-settings

Remember to run nvidia-settings from the terminal with sudo if you want to be able to save any changes you make inside that control panel.

---

### Post by TheUbGuy on 2008-09-06
Thanks. I had actually activated the driver from Harware Drivers and already have nvidia-settings. Like you said, apparently my monitor was not detected properly. By copying over my settings from my OpenSuse xorg.conf, I was able to get running in the proper mode.

---

