---
title: "Issues with Hybird graphics ATi/Intel"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mordanda on 2011-09-08
Hello all,

I've spend the last couple of months poking around this issue, deploying workarounds and whatnot.  Loaded up the beta and I can't seem to fix something that I think is supposed to work.

On 11.10 I cannot get the fglrx driver to work while the laptop is in Switchable Graphics mode, despite the driver's (and internet's) claim that it works.  Laptop boots and installs fine, defaulting to the Intel GPU.  I'm prompted by "Additional Drivers" to install fglrx.  If I install and reboot everything still works, but the Intel chip is still used.  If I do the initial config "amdconfig --initial" I get the following message:

Found fglrx primary device section
Powerxpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialized libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx

After that if I reboot the laptop hangs before LightDM, the last text on the screen being "checking battery state."  I'm pretty sure Powerxpress is what I need so I don't have to set the graphics chip in the BIOS.

Has anyone else seen this and know of a fix or should I file a bug report because something (not me) is really broken?

System Stats:

Lenovo T500 laptop
Ubuntu 11.10 Beta1 64 bit.
GPU1: Intel Mobile 4 Series Chipset
GPU2: ATI Mobility Radeon HD 3650

Any help is appreciated.

Dan

---

### Post by cariboo on 2011-09-08
You will probably want to add your me too, to bug #[lpbug]813809[/lpbug]

---

### Post by pressureman on 2011-09-08
I have a Thinkpad T500 too, with hybrid ATI/Intel graphics. It would be great to get that working properly. I have my BIOS configured 99% of the time for non-switchable, Intel graphics, because if it's on switchable, the ATI GPU seems to run at full speed (even though not in use), gets very hot, and drains the battery. It's very rare that I need to run any high performance graphics apps that warrant switching on the ATI.

Does loading fglrx down-clock the GPU when it's not in use?

---

### Post by mordanda on 2011-09-09
> **pressureman said:**
> I have a Thinkpad T500 too, with hybrid ATI/Intel graphics. It would be great to get that working properly. I have my BIOS configured 99% of the time for non-switchable, Intel graphics, because if it's on switchable, the ATI GPU seems to run at full speed (even though not in use), gets very hot, and drains the battery. It's very rare that I need to run any high performance graphics apps that warrant switching on the ATI.

Does loading fglrx down-clock the GPU when it's not in use?
It's supposed to check at boot if you're plugged in or not.  If you are it'll switch on the ATi and switch off the Intel.  If you're on battery it'll default to Intel.  This is adjustable in the Catalyst Control Center, the only hitch being you need to log out and log back in if you make a change.

I suspect there a symlink not being made correctly which is preventing Powerxpress from accessing the switching libraries, causing the hang if when the power state is checked.

---

### Post by bilal.17 on 2011-09-11
I'm having the same issue as mordanda. If anyone has figured out a solution for this it would be greatly appreciated.

> **mordanda said:**
> result of "amdconfig --initial"

Found fglrx primary device section
Powerxpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialized libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx



---

### Post by r3pek on 2011-09-19
Same problem here. Any solutions?

---

### Post by mordanda on 2011-09-23
Issue still exists in Beta 2.  I've been checking this website "http://www.ubuntuupdates.org/fglrx" looking for updates in the package itself.  I'll file a bug report when I get home this evening.

---

### Post by chlorox on 2011-09-23
I thought the official word from Ubuntu devs was that they were not planning to do anything about it at this time.

I'm in the same boat. When I install fglrx, my system flat out won't do 3D or OpenGL. I have to uninstall it and update alternative back to my intel driver. 

It's not really Ubuntu's fault though. The graphics card makers don't consider Linux support a valuable effort.

---

