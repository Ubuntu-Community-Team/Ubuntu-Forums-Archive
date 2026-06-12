---
title: "Vostro 1500 Video Card Drivers"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Shadow86 on 2008-06-16
Hey, I was wondering if someone could help me. I am trying to set Ubuntu (Gnome) to run using the full effects, however I can't get it to activate. I think it is the drivers and when I attempted to install new ones using Envy or off the Nvidia site I get errors. It loads fine until I get to the log in screen where I can only see white and nothing else. Any help on an easy way to install drivers would be great. I am running Ubuntu 8.04

---

### Post by hitmanh on 2008-06-17
I'm seeing the same issue with my vostro 1500... installed envyng, installed the latest drivers, rebooted the system and end up with a white messy screen instead of gnome login screen.

Cheers

Matt

---

### Post by tenmoi on 2008-06-17
> **Shadow86 said:**
> Hey, I was wondering if someone could help me. I am trying to set Ubuntu (Gnome) to run using the full effects, however I can't get it to activate. I think it is the drivers and when I attempted to install new ones using Envy or off the Nvidia site I get errors. It loads fine until I get to the log in screen where I can only see white and nothing else. Any help on an easy way to install drivers would be great. I am running Ubuntu 8.04

Follow this:

first open synaptics and Completely remove linux-restricted-modules* and nvidia-glx*

sudo apt-get install build-essential libxft-dev
ctrl + alt + f1
sudo /etc/init.d/gdm stop
sudo sh /path_to_your_nvidia.run # case-sensitivity
accept/OK all the way.
sudo /etc/init.d/gdm restart.

If it doesn't solve it, post your /var/log/nvidia-installer.log and /var/log/Xorg.0.log here.

---

### Post by hitmanh on 2008-06-17
> **tenmoi said:**
> Follow this:

first open synaptics and Completely remove linux-restricted-modules* and nvidia-glx*

sudo apt-get install build-essential libxft-dev
ctrl + alt + f1
sudo /etc/init.d/gdm stop
sudo sh /path_to_your_nvidia.run # case-sensitivity
accept/OK all the way.
sudo /etc/init.d/gdm restart.

If it doesn't solve it, post your /var/log/nvidia-installer.log and /var/log/Xorg.0.log here.

Ok, I've just tried the above and get this error:

 Running runtime sanity check:
WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.173.14.09'); assuming successful
         installation.
-> done.

Otherwise the nvidia script ran through. When I start gdm, gnome starts in low-res mode.

This is with 173.14.09 version of the nvidia binary driver.

If I use envyng to remove the driver I can get gnome back to a useful resolution again.

xorg.log shows no errors, I've tried to attach it, but the forum limit is smaller than the log size, and the forum will not let me paste it into the text window.

Cheers

Matt

---

### Post by hitmanh on 2008-06-18
> **hitmanh said:**
> Ok, I've just tried the above and get this error:

 Running runtime sanity check:
WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.173.14.09'); assuming successful
         installation.
-> done.

Otherwise the nvidia script ran through. When I start gdm, gnome starts in low-res mode.

This is with 173.14.09 version of the nvidia binary driver.

If I use envyng to remove the driver I can get gnome back to a useful resolution again.

xorg.log shows no errors, I've tried to attach it, but the forum limit is smaller than the log size, and the forum will not let me paste it into the text window.

Cheers

Matt

I now see the following in my Xorg.0.log

"(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
SetClientVersion: 0 9
SetKbdSettings - type: 80 rate: 30 delay: 500 snumlk: 0
"
the laptop seems to be having issues getting the EDID for the LCD?

Cheers

Matt

---

### Post by Shadow86 on 2008-06-19
I got the exact same result as above.

---

### Post by hitmanh on 2008-06-19
> **Shadow86 said:**
> I got the exact same result as above.

Following the instructions here got it working for me :D

[http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043)

---

### Post by tenmoi on 2008-06-19
> **hitmanh said:**
> Following the instructions here got it working for me :D

[http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043)

and look at post #50

---

### Post by mushroomcloudwarrior on 2008-09-30
> **hitmanh said:**
> I'm seeing the same issue with my vostro 1500... installed envyng, installed the latest drivers, rebooted the system and end up with a white messy screen instead of gnome login screen.

Cheers

Matt

Same problem here. Have you found any solution for this yet?

---

### Post by Shadow86 on 2008-09-30
I used this here: [http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043) and that fixed the error for me. It is important to ensure that you remove all the nvidia drivers and the envyng program first then reboot and continue the installation from the console.

---

