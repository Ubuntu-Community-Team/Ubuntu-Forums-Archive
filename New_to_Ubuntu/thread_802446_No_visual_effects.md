---
title: "No visual effects"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by steve70 on 2008-05-21
I have little issue....

I'm just finished my build, and the upgrade from 7.10 to 8.04 went smoothly.

I do have a problem adding the visual effects...Getting the 'desktop effects not enabled' message when I try to choose the settings.

Here are the basics...

Video Card: NVIDIA GeForce 8400GS
Motherboard: EVGA Ultra 650i 
CPU: (Intel Dual Core 2.2Ghz, Socket 775)
RAM: 2GB DDR2

---

### Post by Therion on 2008-05-21
Have you installed and enabled the Restricted Drivers for your video card?

Example pic:

[IMG]http://farm3.static.flickr.com/2162/1956524075_66927b0e7a.jpg[/IMG]

---

### Post by anotherdisciple on 2008-05-21
Under System>Preferences>Appearance are the effects set to "none"? I would think that the compiz settings manager would override this, but maybe not.

---

### Post by littletinman on 2008-05-21
I had the same problem. My Nvidia card wasn't showing up in the drivers manager. Installing Envy helped and fixed everything.

---

### Post by RedRat on 2008-05-21
> **steve70 said:**
> I have little issue....

I'm just finished my build, and the upgrade from 7.10 to 8.04 went smoothly.

I do have a problem adding the visual effects...Getting the 'desktop effects not enabled' message when I try to choose the settings.

Here are the basics...

Video Card: NVIDIA GeForce 8400GS
Motherboard: EVGA Ultra 650i 
CPU: (Intel Dual Core 2.2Ghz, Socket 775)
RAM: 2GB DDR2

Ok had a similar problem and let me insert here an answer I gave to someone else on this forum:

A bit of a warning here that I have had with nvidia proprietary drivers and settings. I stumbled on this just this week to get the resolutions to work correctly. At least in my case with 7.10 and 8.04 upgrade, the System>Preferences>Screen Resolution do not appear to be talking correctly with nvidia driver. I found that I needed to download "nvidia-settings" from Synaptic. For reasons that are not clear to me, the "Screen Resolution" and nvidia driver do not seem to work well together (e.g., I have scans of 51, 50, or 107 Hz--go figure--even though the monitor is correctly identified in xorg.conf and all the allowable scan rates and resolutions are correctly spelled out.). Below is the only way I can get compiz to work on my system. 

In order to get "nvidia-settings" to be able to write to the xorg.conf file you need to run this program using the following command:
1. hit <alt><F2> this brings up a run line window.
2. enter the following: gksudo nvidia-settings
3. enter whatever resolutions and scan rates that are appropriate and then save the settings. 

You need to do run it as gksudo in order to pass write privileges so that nvidia-settings can write the xorg.conf backup file. Merely running the program will change your desktop settings but when you reboot you will fall back to whatever was in xorg.conf to start with. I strongly suggest that you read the following web page:
[www.psychocats.net/ubuntu/permissions](www.psychocats.net/ubuntu/permissions)

In order to access certain files you need to do this with root privileges. As you will see on that page you can also run nautilus (if you are running Ubuntu) or Konquerer if you are running Kubuntu, etc. or whatever file manager you use. 

Hope this helps.

---

### Post by steve70 on 2008-05-21
> **littletinman said:**
> I had the same problem. My Nvidia card wasn't showing up in the drivers manager. Installing Envy helped and fixed everything.


Thanks a lot on the info. went to envy, installed it, and got my stuff going!

---

### Post by littletinman on 2008-05-21
You're very welcome. Don't forget to use the thank button (the little medal) when someone helps you. It's like giving them money without any hurt to your wallet.

---

