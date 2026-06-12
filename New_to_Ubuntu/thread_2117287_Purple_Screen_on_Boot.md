---
title: "Purple Screen on Boot"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by Berslythe on 2013-02-18
Hello everyone on the Ubuntu forum
I recently installed Ubuntu 12.04 LTS on my Acer 5542G. It worked perfectly, I could do everything great, and I really like the OS. Now, I won't lie, I only came to Ubuntu for the free item in TF2. But, after experiencing it, I quite like how it works, and am interested in learning more about it. I honestly wanted to install it for a while, and the item was the push I needed. So, back to my problem. I went into Ubuntu for the first time, I updated a bunch of stuff from the Update Manager, and I installed Steam. Now, when I opened steam, it asked me to install some drivers for my graphics card (An ATI Mobility Radeon 4570 HD), and I pressed accept, thinking it was a routine driver upgrade. Then, I was asked to reboot, so I did, and that's when the problems started. I was greeted by a blank purple screen when the computer started back up. I let it sit for a good 20 minutes, thinking maybe it was installing the new updates in the background or something, but then I gave up and had to shut it down manually. I really want to get this working, since I want to get to know how to use all this. Any help would be great :) By the way, if you haven't already figured it out from the forum, this is my first time with Ubuntu, and I have pretty much no knowledge of what to do. The extent of my adventures with Ubuntu was installing the 32 bit libs for Steam to work. (I'm on a 64 bit system. I don't know if this broke it either.)

Now, some stuff which might help:
Processor: AMD Athlon II X2 M300 @ 2 GHz
Graphics: ATI Mobility Radeon 4570 HD
64-bit Ubuntu 12.04 LTS
I'm dual booting it with Windows 7 Home Premium 64-bit
I have 10GB for the /root partition
500MB for the  /boot partiton
5GB for swap
and 25GB for the /home partiton

---

### Post by Berslythe on 2013-02-18
Bump :D

---

### Post by mörgæs on 2013-02-18
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Berslythe on 2013-02-18
Thanks for the link :)
I tried doing some of the steps, but got confused at Step 3.

Step 3. From the Grub Menu, try to boot in Rescue mode/low graphics.
- If Yes, look for additional drivers and install recommended driver.
- If No, goto Step 4 to verify that linux kernel will boot.

I made my way to the Menu, but couldn't find out how to boot it in Rescue mode/low graphics.

---

### Post by grahammechanical on 2013-02-18
Let us start from the beginning.

You get the grub menu? Yes? Look for Recovery Mode in the list of kernels to boot. Select it and boot it. The line might read something like: Ubuntu with Linux 3.2.0-21 (recovery mode). 

At the next screen select failsafeX to run in fail safe graphic mode. I find that selecting Resume sometimes will get me to a desktop as that loads Ubuntu without activating video driver. It is most likely the video driver that is causing this problem.

They are not open source code and their is nothing much the Ubuntu developers can to correct the fault.

Regards.

---

### Post by Berslythe on 2013-02-19
Alright, I went into recovery mode and went into failsafeX.
Nothing really happened, it said Fatal server error: no screens found
Please also check the log fie at "/var/log/Xorg.failsafe.log" for additional information
ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file

I gather this is a bad thing? Sorry for the late reply as well, sleep and school got in the way.

Edit: I also tried Resume Boot from the recovery menu, and this just froze on a black screen.

---

### Post by mörgæs on 2013-02-19
Ubuntu is more demanding than for example Xubuntu with regards to graphics drivers, and the 'purple haze' is not likely to happen in the latter.

If you are new to Buntu, as your first post indicates, an easy test is to try Xubuntu 12.04 or 12.10 (including all updates, which come automatically). Best is to let the system run for some time without adding closed-source drivers.

---

