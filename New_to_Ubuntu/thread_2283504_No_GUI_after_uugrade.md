---
title: "No GUI after uugrade"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by DGINSD on 2015-06-22
I upgraded via  the Software Update program from Ubuntu 14.04 to 14.10 everything seemed to go fine till after the reboot. the system froze at the Ubuntu logo with the orange cycling dots under it. eventually this will go away and leave me a totally blank screen.


If I ```
ctrl alt F1
``` to tty1 and login (I can login just fine) I get some error out put like this

```

[   170.795975] systend-logind[1113]: Failed to run unit user@1000.service:  Unknown unit user@1000.service  
[   170.796118] systend-logind[1113]: Failed to run user service:  Unknown unit: user@1000.service

```

What this means I don't know I'd like to avoid a complete reinstall, things seem to work ok on the command line but I get on GUI

---

### Post by dino99 on 2015-06-22
why not using 'upstart' to boot (advanced) instead of 'systemd' ?
and glance at possible broken links inside /etc/rc?.d folders (they can be erased safely)
have you cleaned the system ? (clean/autoclean/autoremove)

---

### Post by grahammechanical on 2015-06-22
Ubuntu 14.10 will reach end of life by the end of July 2015

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You will have to upgrade to 15.04. I suggest that you make safe backups of all data that you do not want to lose and think seriously about re-installing either 14.04.2 and waiting until Ubuntu 16.04 LTS is released, or installing Ubuntu 15.04, which will mean upgrading to 15.10 and then 16.04.

It is likely that the same problem will be there after an upgrade. But it is unlikely that this problem will be there after a fresh install.

Do you get to a login screen? Or is the system set for automatic login? Are you using a proprietary video driver? If so you may need to purge it and use the default open source video driver.

You could try from the Grub boot menu selecting Advanced options for Ubuntu and then selecting Recovery Mode. At the recovery menu the Resume option will load using a fall back open source video driver. If that gets you to a working desktop then try changing video drivers.

Regards.

---

### Post by DGINSD on 2015-06-22
I was originally on 14.04 and got myself in this mess by using a command to upgrade to 14.14.2 that caused issues with the proprietary graphics drivers (FGLRX) at which point I  tried to uninstall them and go back to the open source drivers, this didn't work so good, I finally through a bunch of tinkering got FGLRX drivers to mostly work, then I did the full upgrade to 14.10 which was all Software Update offered to me, which left me at this state.

I can now install either the open source or proprietary drivers but both leave me in this state where all that's useable is a cli environment

---

### Post by DGINSD on 2015-06-23
When I got home, I thought that when trying to upgrade to[COLOR=#000000] 14.14.2 I was actually bringing my kernel and xserver up to where 15.04 is so I ran 

```
sudo run-distribution-upgrade
```

this actually brought my GUI to a working state, and put me on 15.04.  I'll have to prod around to see if there's anything else that's broken. 

This was my first time trying to stay on a LTS version till the next LTS was released and I would  of liked to continue on, why are the LTS versions not brought up to the next point release automatically from 14.04 to[/COLOR][COLOR=#000000] 14.04.1 and on to[/COLOR][COLOR=#000000] 14.04.2?  If they are how do you tell, this confused me quite a bit. [/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by mansonfan78 on 2015-06-23
The xserver was a constant source of problems on my old desktop, updates were always breaking the display.  I ended up version-locking the xserver and never had any more problems (until the next upgrade).

---

### Post by DGINSD on 2015-06-23
That'sThat's an interesting idea, it always seemed the issue was caused when the kernel upgraded not the xserver but I could be wrong. How would I go about trying locking the xserver version?

---

### Post by mansonfan78 on 2015-06-23
If you have Synaptic installed you could launch it, search for "xserver", highlight the entry,  go to "package" - "lock version".  You would have to unlock any locked packages before upgrading the system.

---

### Post by Ty_Scheun on 2015-06-23
When you boot, do you go into a terminal screen, if so, enter in the following command

```
sudo apt-get install lubuntu-desktop-environment
```

---

### Post by DGINSD on 2015-06-23
> **mansonfan78 said:**
> If you have Synaptic installed you could launch it, search for "xserver", highlight the entry,  go to "package" - "lock version".  You would have to unlock any locked packages before upgrading the system.

Ok another question  if I lock the xserver version do I need to do that before or after I install the FGLRX proprietaty driver or does it even matter? Also the package I should be locking is xserver-xorg and by locking that package it should also lock all the xserver hardware variants?

---

### Post by mansonfan78 on 2015-06-23
It shouldn't matter if you do it before or after.  "xserver-xorg" should be the only one you need to lock, it wouldn't hurt anything to lock the hardware variants (so, if in doubt, you can safely lock everything that has "xserver" in it's name).  You'll just have to remember to unlock them when you upgrade, thankfully Synaptic has a search feature to locate all locked packages (you should be able to figure out how to do that easily enough).

---

