---
title: "Toshiba Satelite A70 information"
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by gregh on 2005-03-28
I am posting this information so others may benefit from my trials with this laptop.
If a subject/device is not mentioned, it either worked out the box or I have not had reason to use it.

ACPI. This only partially works because this laptop has a Phoenix BIOS. Battery monitor works but fan control does not.

CPU Scaling. Powernowd does not work with this model, you need to use cpufreqd is you wany dynamic cpu scaling. Cpufreq works fine.

Touchpad: You must disable "legacy USB support" in the BIOS (press F2 when first powering on the laptop)

FNFX: (Toshiba hotket utility) Does not work with this model

Module toshiba_acpi will not work (phoenix BIOS)

Modules p4_clockmod, freq_table and speedstep_lib work and should be loaded.

ATI binary driver (firegl) will work but locks the laptop when attempting to run 3D (DRI) games/applications.
You can only use the xorg driver (ati) for 3D stuff.
To improve 3d performance add these lines to the "Device" section:
Option "AGPMode" "4"
Option "AGPFastWrite" "True"
Option "EnablePageFlip" "True"


Suspend to Disk will go through the suspend process fine and power off, but will not come back properly. It knows its suspended and tries to reload, but it ends up with a black screen and locked up laptop.
Suspend to RAM does not work.

SOUND: If you include snd_atiixp_modem and snd_atiixp in the /etc/hotplug/blacklist and add snd_atiixp in the /etc/modules at the end of the module list the sound seems to load most of the time ok.

Thats all for now I hope it will save some folks time when trying to get some of this laptops features to work.

-Greg

---

### Post by somuchfortheafter on 2005-03-28
Same goes for the tecra m2 everyone well except for alsa worked in warty, now im using esd.

---

### Post by aburda on 2005-03-31
Since we are speaking about Toshiba laptops....

I have an A10 that I am trying to resolve performance issues with.

The first issue is the video performance which is abysmal.  The system has an intel video card (Intel 852GM Chipset???) which works "decently" under windows for 3d but can hardly run any of the 3d screen savers in gnome.

I found a site that has recommendations for how to setup the video card for some obscure distro but I need to edit the /etc/X11/xorg.conf which doesn't seem to exist in ubuntu (did a find on the /etc and ~ directories and can't find it.)  

Here is the site

[http://cold.sunsite.dk/toshiba/#BIOS](http://cold.sunsite.dk/toshiba/#BIOS) 


I just recently upgraded to the i686 kernel through apt-get but should I still do a complete recompile of the kernel to tailor it to my laptop?  More info related to the AGP bus would be useful.


Boot-up time is deffinately slower, but I'm playing with the rc files to tune this as best as possible.

OpenOffice is abysmal (The beta 2 from apt-get), which confuses me a bit, I would think that the people over at OO would have the linux version tuned to the hilt in comparison to the Windows version.

Any other recommendations on how to tune ubuntu to the max would be much appreciated.

On the upside Eclipse is 15x faster than in windows and once everything is up (besides OpenOffice) the system is much more responsive than windows.

Aaron

---

### Post by m2mike on 2005-04-01
If anyone knows how to get a PCMCIA Cisco LMC352 card to work in a Toshiba Satellite A75 or similar model of laptop, then please post here or pm me.  I have been playing with the live CD's.  Aside from the Cisco card, the integrated wireless is not detected by either the Hoary 5.04 or Warty 4.10 versions.  That happens to be desirable for me because I have no use for it anyway.

I did get my touchpad working by disabling "Legacy USB Support" in the BIOS so thank you for that.

*Edit*

I got my Cisco 352 working.  After booting from the Hoary 5.04 live cd, I simply waited for everything to load and then ejected and re-inserted my cisco card.  Then I did a "ifconfig -a" and a "iwconfig" to make sure that it could be "seen".  After that it was simple as "iwconfig eth1 essid essidname key blahblahblah".  It now works.

The integrated card still does not work, but hopefully that will be solved soon as well.  Other than that everything seems to work smoothly.

My only other complaint is that there is no gcc compiler with the live cd and Rhythmbox can't play mp3's.  Other than that, it is a decent distro and one of the more user friendly I have seen.

---

### Post by WiFi Net Guy on 2005-04-19
[QUOTE=m2mike]If anyone knows how to get a PCMCIA Cisco LMC352 card to work in a Toshiba Satellite A75 or similar model of laptop, then please post here or pm me.  I have been playing with the live CD's.  Aside from the Cisco card, the integrated wireless is not detected by either the Hoary 5.04 or Warty 4.10 versions.  That happens to be desirable for me because I have no use for it anyway.

I did get my touchpad working by disabling "Legacy USB Support" in the BIOS so thank you for that.[/QUOTE]
 m2mike,

I have a Toshiba Satellite A75 also, I'm working off of my integrated wireless card under Hoary 5.04. It works great! If you haven't gotten yours working yet, I'll be glad to help any way I can.

---

### Post by gregh on 2005-04-19
Here is another strange little "quirk", after you change the BIOS setting to disable legacy support (required to make the touch pad work), the laptop will no longer perform a "shutdown" from the log off menu.

It does everything except powering off!!

If you re-enable legacy support, it will shutown AND power off.

Go figure, it must be to do with the crappy phoenix bios

Shame, I like my Toshiba, but with such erratic support for linux, I will have to look at other when I do a laptop refresh later this year.

---

### Post by m2mike on 2005-04-23
[http://www.fedorafaq.org/#otherinstall](http://www.fedorafaq.org/#otherinstall)

Click on the above link for a possible solution for getting the mouse to work.  The same methods for Fedora may be able to be used with Ubuntu.

---

### Post by snaga on 2005-05-02
[QUOTE=gregh]It does everything except powering off!!

If you re-enable legacy support, it will shutown AND power off.
[/QUOTE]

I'm using an A75. I have this same problem, except its with restart. It powers off fine, but won't restart. I tried the fedora solution above, but unfortunately it didn't work.

Any more ideas to get the touchpad to work without sacrificing restart/powerdown capability? I don't restart too often, so I can live with it, but it would be nice to have that ability.

dm

---

### Post by wxm505 on 2005-05-13
[QUOTE=aburda]Since we are speaking about Toshiba laptops....

I have an A10 that I am trying to resolve performance issues with.

The first issue is the video performance which is abysmal.  The system has an intel video card (Intel 852GM Chipset???) which works "decently" under windows for 3d but can hardly run any of the 3d screen savers in gnome.

I found a site that has recommendations for how to setup the video card for some obscure distro but I need to edit the /etc/X11/xorg.conf which doesn't seem to exist in ubuntu (did a find on the /etc and ~ directories and can't find it.)  

Here is the site

[http://cold.sunsite.dk/toshiba/#BIOS](http://cold.sunsite.dk/toshiba/#BIOS) 


I just recently upgraded to the i686 kernel through apt-get but should I still do a complete recompile of the kernel to tailor it to my laptop?  More info related to the AGP bus would be useful.


Boot-up time is deffinately slower, but I'm playing with the rc files to tune this as best as possible.

OpenOffice is abysmal (The beta 2 from apt-get), which confuses me a bit, I would think that the people over at OO would have the linux version tuned to the hilt in comparison to the Windows version.

Any other recommendations on how to tune ubuntu to the max would be much appreciated.

On the upside Eclipse is 15x faster than in windows and once everything is up (besides OpenOffice) the system is much more responsive than windows.

Aaron[/QUOTE]

I have to say please do not follow the guide of how to configure ur graphics card
by the link mentioned above. I tried it.Then I can not start X.

---

### Post by Elv13 on 2005-08-31
about wireless, do it work for other a70 user?

---

### Post by niobe_logos on 2005-09-04
I don't know about the A70, but I have an A65, and wireless worked flawlessly out of the box. The A65 has this quirky thing with a hardware on/off switch for the wireless card. If the card is not turned on, Ubuntu won't try to do anything with it. I guess the switch is useful for making the battery last longer, or something. 

One thing I noticed is that for wireless, I need to open up the network configuration box frequently in order to get the wireless card to wake up and look at the network I want it to see. Same thing for the network connection icon in the toolbar: if you don't set it to the connection you're working with (eth0, ath0, or whatever), it'll just report on the useless Io port (127.0.0.1), letting you know over and over again that you have a working network card.

Most other things worked either "out of the box" or after I worked my way through the Unofficial starter guide, with the exception of toshiba-utils (so no screen brightness adjustment) and having a USB headset work. If you have any clues as to how I can get the headset to work *and* keep my onboard sound the way it is, let me know.

---

### Post by snaga on 2005-09-08
[QUOTE=Elv13]about wireless, do it work for other a70 user?[/QUOTE]

Wireless works fine on my A70. I don't recall doing anything out of the ordinary to get it going.

---

### Post by Elv13 on 2006-01-09
newer MM kernel can load touchpad with usb legacy on, but touchpad special option dont work...

---

