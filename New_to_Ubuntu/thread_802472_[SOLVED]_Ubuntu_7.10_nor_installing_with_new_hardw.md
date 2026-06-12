---
title: "[SOLVED] Ubuntu 7.10 nor installing with new hardware"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-05-21
Just got my new hardware this morning  {8 ^,  

MSI K9NGM4-F V.2 mobo
Athlon64 2.4GHz cpu
1GB Kingston DDR2 800MHz PC2-6400
old Samsung CD drive     (for testing only)
old Seagate medalist Pro (for testing only)
Enlight 350W PS

Ubuntu 7.10 is not co-operating. Ubuntu 7.10 seems to be installing just fine. A message opens that states "your screen & graphics card could not be detected correctly" and then uses low res graphhics (probably to be expected since the on-board video is Geforce 7025?). I click continue and all seems well. It starts to run various checks but hangs on the following:

running local boot scripts (/etc/rc.local)

it's been on that command longer than it took me to type out this help request and it doesn't seem to be progressing further anytime soon without some assistance. Thank for your assistance.

ps someone at Newegg wrote a review of this mobo and said Ubuntu 7.10 loaded without a hitch

---

### Post by cmnorton on 2008-05-21
Try the "alt-mode" or command line only installation. If you have to resort to command line, you can get your network working and then install the Ubuntu desktop (gnome).

Does this system boot with the live CD or with Knoppix?

Ubuntu 7.10 had a difficult time working with my nvidia card. The alt-mode install worked fine.

---

### Post by shifty_powers on 2008-05-21
well for a start what grpahics are you actually using?

and have you tried envy?

```
sudo apt-get install envyng-gtk
```

---

### Post by Samurai Penguin on 2008-05-21
I haven't gotten to the desktop yet. 

what's an Alt-Mode?

How do I do that? 

Here's the scoop - The 7.10 OS will not install. It needs to make it to the desktop so that I can click the INSTALL icon. 
Doesn't make it to that point right now.
I'm using the CD I downloaded as an ISO and burned to a CD (so I'll guess that's what is called a "live CD" ?). I'm almost sure it's the make/model of motherboard, I've seen the same thing happen with a Gigabyte mobo I once tried. This MSI Mobo with built-in Geforce 7025 graphics is an AM2+/AM2 mobo so it's fairly new.

---

### Post by RedRat on 2008-05-21
> **Samurai Penguin said:**
> Just got my new hardware this morning  {8 ^,  

MSI K9NGM4-F V.2 mobo
Athlon64 2.4GHz cpu
1GB Kingston DDR2 800MHz PC2-6400
old Samsung CD drive     (for testing only)
old Seagate medalist Pro (for testing only)
Enlight 350W PS

Ubuntu 7.10 is not co-operating. Ubuntu 7.10 seems to be installing just fine. A message opens that states "your screen & graphics card could not be detected correctly" and then uses low res graphhics (probably to be expected since the on-board video is Geforce 7025?). I click continue and all seems well. It starts to run various checks but hangs on the following:

running local boot scripts (/etc/rc.local)

it's been on that command longer than it took me to type out this help request and it doesn't seem to be progressing further anytime soon without some assistance. Thank for your assistance.

ps someone at Newegg wrote a review of this mobo and said Ubuntu 7.10 loaded without a hitch
When you do get your card detected you will probably need to download the nvidia drivers if they are not already installed. A bit of a warning here that I have had with nvidia proprietary drivers and settings. I stumbled on this just this week to get the resolutions to work correctly. At least in my case with 7.10 and 8.04 upgrade, the System>Preferences>Screen Resolution do not appear to be talking correctly with nvidia driver. I found that I needed to download "nvidia-settings" from Synaptic. For reasons that are not clear to me, the "Screen Resolution" and nvidia driver do not seem to work well together (e.g., I have scans of 51, 50, or 107 Hz--go figure--even though the monitor is correctly identified in xorg.conf and all the allowable scan rates and resolutions are correctly spelled out.). Below is the only way I can get compiz to work on my system. 

In order to get "nvidia-settings" to be able to write to the xorg.conf file you need to run this program using the following command:
1. hit <alt><F2> this brings up a run line window.
2. enter the following: gksudo nvidia-settings
3. enter whatever resolutions and scan rates that are appropriate and then save the settings. 

You need to do run it as gksudo in order to pass write privileges so that nvidia-settings can write the xorg.conf backup file. Merely running the program will change your desktop settings but when you reboot you will fall back to whatever was in xorg.conf to start with. I strongly suggest that you read the following web page:
[www.psychocats.net/ubuntu/permissions](www.psychocats.net/ubuntu/permissions)

In order to access certain files you need to do this with root privileges. As you will see on that page you can also run nautilus (if you are running Ubuntu) or Konquerer if you are running Kubuntu, etc. or whatever file manager you use. 

Hope this helps.

---

### Post by Samurai Penguin on 2008-05-21
I'm presuming that you're saying Ubuntu 7.10 will not complete booting from the CD to the desktop because it needs to see a graphics solution? There is a  solution - Geforce 7025 ON-BOARD chipset.

I have a pci graphics card. Maybe I should install it and if things install ok ... 

How do I get the Geforce 7025 on-board graphics to be recognized?

I'm not being given a solution here folks and its been many hours. Well, thanks anyway. Bye

---

