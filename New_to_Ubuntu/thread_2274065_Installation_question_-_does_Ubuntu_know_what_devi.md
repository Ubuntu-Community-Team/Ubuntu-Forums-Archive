---
title: "Installation question - does Ubuntu know what devices I have and installs drivers?"
date: 2015-04-17
forum: New to Ubuntu
---

### Post by richlion2 on 2015-04-17
Hello, 

I am pretty new to Ubuntu, using actually Kubuntu and recently Lubuntu. My question is rather a generic one. 
When installing Ubuntu are devices being discovered during the process and configured? How does this work?

Let's say for example I have 2 graphics cards, one on-board with an RGB socket and another PCI-E card, like
Nvidia or ATI Radeon HD. I know that there is a generic driver called Nouvau and it is enabled when I have an
Nvidia graphics cards, so to use it additional card I need to enable it and choose which driver I would like to 
use. What about the ATI graphics cards? 
I read that usually the installer installs some drivers and things should work out of the box (a lot of drivers
installed already) , so if I have an ATI Radeon graphics card plugged in I should not need to install any propriety drivers. 
Which means somehow the installer knows what graphics card I have and configures the system to use it?

So how does this work?

Thanks in advance for helping. 
Richard

---

### Post by Vladlenin5000 on 2015-04-17
Linux kernel includes a lot of drivers already and some distros like Ubuntu make it easy for users to load additional proprietary drivers and/or firmware to support many more.
Indeed it tries to install right away as many hardware as it has drivers for and it usually works fine out of the box. However, in some case we need to use different drivers, often proprietary, for better performance.
There are open source drivers both for Nvidia (*nouveau*) and AMD (*Radeon*). Some newer cards/chips may not be supported and some older ones are considered legacy and have support only via the open source drivers. As such there can't be a straight answer to your question. Better give real examples and then someone might be able to tell you what works better.

---

### Post by SeijiSensei on 2015-04-17
The application called either "Additional Drivers" or "Driver Manager" is designed to scan your hardware and install any proprietary drivers you may need.  My Kubuntu 14.04 system has Driver Manager as part of System Settings.

---

### Post by richlion2 on 2015-04-20
Hello, 

I'll rephrase my question then. 
If I have an old PC with a standard RGB monitor socket and want to buy and install an ATI Radeon graphics card, do I install the system from scratch having the card already plugged in, or do I just plug in the new card and open the KDE (this is on Kubuntu) "Device Manager" to switch to the new card? 

Regards, 
Richard

---

### Post by richlion2 on 2015-04-20
Thanks for your reply. 
So if I buy a new ATI Radeon graphics card I can plug it into the system without reinstalling it?
I can then run the KDE "Device Manager" to switch to the recommended driver?
This site seems to explain it, my question was about the installation phase. 
[http://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/](http://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/)

Regards, 
Richard

---

### Post by Bucky Ball on 2015-04-20
> **richlion2 said:**
> So if I buy a new ATI Radeon graphics card I can plug it into the system without reinstalling it?

Yes. Insert the new card, boot the machine. You may not need to do anything more than that. The system will pick up the card on boot and load the appropriate drivers, if they are in the kernel. If they are not, then go the 'Additional Drivers' route.

Insert the card, boot, and let us know what happens. There is NO need to reinstall Ubuntu at this stage (and probably any other in regards to this issue).

---

### Post by mastablasta on 2015-04-22
> **richlion2 said:**
> Hello, 

I'll rephrase my question then. 
If I have an old PC with a standard RGB monitor socket and want to buy and install an ATI Radeon graphics card, do I install the system from scratch having the card already plugged in, or do I just plug in the new card and open the KDE (this is on Kubuntu) "Device Manager" to switch to the new card? 

Regards, 
Richard

you plug it in and it will get recognised.

however beware with old systems. New AMD cards that support PCIe3.0  and 2.0 do not support old PCIe 1.1. New NVidia cards that support PCIe 2.0 do support old PCIe 1.1 plug, however I still had problem, installing it. though it was recognised I couldn't get the drivers load properly. troubleshooting also failed. motherboard BIOS was form 2009, board was a few years older when it came out.

therefore if you plan on upgrade do your homework and if PC is really old then you might be stuck with old GPU or at least an older model.

you can see what is happened at boot if you type dmesg in konsole or if if you check the logs (e.g. with log viewer). it says exactly which hardware was found and what drivers were loaded.

edit: unlike in windows drivers are part of kernel. so kernel probes for hardware and just loads the needed drivers. problem with this solution is sometimes it mislabels the hardware and loads wrong drivers, sometimes it recognises the hardware correctly but then goes and loads wrong drivers. in both cases there are ways to force the kernel to load correct things if the issue appears.

---

### Post by grahammechanical on 2015-04-22
May I add my advice?

Before you install the new video adapter card go Additional Drivers or Driver manager, if that is what it is called in Kubuntu and change the existing video driver to the open source video driver. The existing video card driver if it is a proprietary video driver will be set up for the existing video card. It may cause a problem, especially if the new card is from a different manufacturer to the old card.

Then once you have installed the new adapter and restarted you can go again to Additional Drivers and select a proprietary video driver if that is your wish.

Regards.

---

### Post by Bucky Ball on 2015-04-22
> **grahammechanical said:**
> May I add my advice?

Before you install the new video adapter card go Additional Drivers or Driver manager, if that is what it is called in Kubuntu and change the existing video driver to the open source video driver. The existing video card driver if it is a proprietary video driver will be set up for the existing video card. It may cause a problem, especially if the new card is from a different manufacturer to the old card.

Then once you have installed the new adapter and restarted you can go again to Additional Drivers and select a proprietary video driver if that is your wish.

Regards.

+1. Good thinking.

---

