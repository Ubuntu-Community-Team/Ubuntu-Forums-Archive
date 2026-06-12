---
title: "Ubuntu on HP Compaq D530..."
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Jancarel on 2008-10-06
Dear Ubuntu Friends,

I have installed Ubuntu on a few computers now and I never had any problems. I bought myself a used HP Compaq D530 computer and I tried to install Ununtu. The installation process just locks up. I cannot get the installation to finish. The harddisk is empty and Ubuntu will be the only system on this computer. I noticed that during the installation the HD LED did not blink, as if there is nothing written to the disk. The CD drive light blinks, but nothing is copied to the harddisk. Is there anyone out there with Ubuntu installed on a HP D530. If so, did you change any setting in the BIOS to get this to work...

Thank for your help,

Jan

---

### Post by Thelasko on 2008-10-06
HP laptops are notorious for problems with Ubuntu.  [Here's a tutorial]("http://ubuntuforums.org/showthread.php?t=793553") and I also recommend the alternate CD.

---

### Post by shifty_powers on 2008-10-06
have you tried the alternate install cd?

it has no gui, but is easy to use and will often work where the live cd doesn't.

[http://cdimage.ubuntu.com/hardy/daily/current/](http://cdimage.ubuntu.com/hardy/daily/current/)

---

### Post by shifty_powers on 2008-10-06
funny, my hp latop works like a dream with kubuntu (8.10) :D

---

### Post by Thelasko on 2008-10-06
> **shifty_powers said:**
> funny, my hp latop works like a dream with kubuntu (8.10) :D

Don't kill the messenger.  It's just what I've heard.  The problems usually occur with the DV9000.

Just remember, problems in Linux are not insurmountable.  It's just takes more effort to get it to work.

---

### Post by ToasterThief on 2008-10-17
> **Thelasko said:**
> HP laptops are notorious for problems with Ubuntu.  [Here's a tutorial]("http://ubuntuforums.org/showthread.php?t=793553") and I also recommend the alternate CD.

A HP/Compaq d530 is a desktop, not a laptop. That aside it runs just fine with both Gutsy and Hardy. It sounds like the the problem is hardware rather than Ubuntu. The only problem I have encountered with HP d530s is poor fan control (fans running max. at low temp).

---

### Post by Jancarel on 2008-10-23
> **ToasterThief said:**
> A HP/Compaq d530 is a desktop, not a laptop. That aside it runs just fine with both Gutsy and Hardy. It sounds like the the problem is hardware rather than Ubuntu. The only problem I have encountered with HP d530s is poor fan control (fans running max. at low temp).

Hi ToasterThief,

Yes you are right, the D530 is a desktop, not a laptop. Can you tell me if you have a SATA or a PATA harddisk installed in your D530. If you have a PATA (parallell interface), can you tell me what setting you use in your BIOS. I am trying to install Ubuntu on my D530 (PATA), but the installation crashes. Yes, the problem must be hardware related. Probably a setting in the BIOS. I have installed Ubuntu on several other computers, I never had a problem...

Thanks,

Jan

---

### Post by gmcalp on 2009-03-16
I just installed Intrepid on a HP/Compaq D530 last night. I used the alternate DC (it's the only one I had lying around) and the install went just fine. I am using a PATA drive (it's the only one I had, and it was already installed). The only problem I am having now is with sound. For some reason only the internal speaker is putting out any audio, neither the front nor the rear speaker/headphone jacks seem to be working correctly. Well, they are working, but any audio that comes out is also coming out of the internal PC speaker too... not sure how I will fix that one... I guess it's time to start poking around some more. :)

---

### Post by Mttechserv on 2009-04-05
Hey-o!
Did you manage to fix the sound output issue?
I also have an HP/Compaq D530 Tower. Works great, except the only sound is from the internal speaker, nothing from speakers. A little annoying at best. 
( This was happening with both 8.10 and 9.04 - Just updated a few minutes ago, no change )

Any information would be much appreciated,
Matt

---

### Post by halitech on 2009-04-05
whats the output of ```
lspci
``` and ```
lshw -C sound
```

---

### Post by Mttechserv on 2009-04-05
Nvm... 
Managed to fix it using this :
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

A little tweaking is needed... but I think I'll manage. :-D

---

### Post by ziqbal on 2009-08-06
Hi Gurus,

Just installed 9.04 on my HP D530. I am trying to get the Visual effect enable so that i can run gnome-do in docky mode. But it wont enable the desktop effects. Any help or tip. Any special driver that I would need on this machine.

Thanks

---

### Post by Mttechserv on 2009-08-06
That would all depends on what you're using for video. 
Can't remember off the top of my head what the D530 has onboard... in my case, I'm actually using an Nvidia card.
I think it's an Intel Extreme chipset. 
If so, you might be out of luck... as per this :
[http://howflow.com/tricks/ubuntu_9_04_intel_graphic_drivers_enable_desktop_effects_fix](http://howflow.com/tricks/ubuntu_9_04_intel_graphic_drivers_enable_desktop_effects_fix)

Cheers,
Matt

---

### Post by ziqbal on 2009-08-07
Hi Matt,

Thanks for the reply. I do have Intel 82865G Integrated Graphic controller (rev 02). so as per your suggestion it wont work. 

Regards


Zahid

---

### Post by seldon77 on 2010-01-16
> **ToasterThief said:**
> The only problem I have encountered with HP d530s is poor fan control (fans running max. at low temp).

I had this problem too...

Manually changed fan speed as such:

```

#echo 1 > /sys/class/hwmon/hwmon0/device/pwm1_enable
#echo 70 > /sys/class/hwmon/hwmon0/device/pwm1

```

(change 70 to whatever speed)

put into /etc/rc.local for every bootup

---

