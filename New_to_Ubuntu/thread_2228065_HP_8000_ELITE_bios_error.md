---
title: "HP 8000 ELITE bios error?"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by StewartKMorganza on 2014-06-05
Okay to make it short my old computer died the other day so I bought a HP 8000 elite, 3.17ghz duel cpu, 6gb ram, 1tb hard drive, 1gb radeon HD4650 video card for $280.

I tried to install steamos on it, but I found out that the video card is not supported yet(I think) and went back to ubuntu for until they add support.  I have another video card, a nvidia 9500GT, and tried to install it as well so that I could have a second monitor going, but it didn't play nice with the radeon card so I removed it and removed the nvidia driver. . well now my radeon isn't working and it's just a blank screen on loading.  I think it may be the bios or something, cause I've seen that problem before, but since this is a brand new computer I don't have a copy of the bios and the copy that I downloaded I don't think is the right kind.

---

### Post by grahammechanical on 2014-06-05
Why would it be the BIOS? Did you change BIOS settings when you added that second video card? Perhaps you need to reset those settings. You can also try recovery mode under the Advance Options in the Grub menu. And at the recovery menu select Resume. That may get you to a desktop with an open source video driver.

---

### Post by StewartKMorganza on 2014-06-05
You're probably right; this doesn't seem anything like a bios error.  Also I can't even get to grub unfortunately; when I turn on the computer it doesn't connect to the monitor.  If I try it with both video cards in nothing; if I try it with one or the other video cards nothing.

I know it's not a hardware failure cause this computer is right out of the box and was working; it's probably not the bios cause it's not a blank screen that normally is a bios error so much as the monitors don't even turn on and I know those work, but I can't even get into grub.

---

### Post by StewartKMorganza on 2014-06-05
Now that I think about it it's probably just that my computer isn't recognizing the video cards.  It sounds like it's booting up and such; that's probably just it.

I'm probably going to need some help.  I'm probably going to have to log in without using the monitors; use terminal, purge the drivers and then reinstall the nvidia driver.  I would install the radeon driver, but I'm probably going to need help doing that cause that's where everything messed up.

Can someone paste the terminal commands to purge nvidia and amd drivers?  I haven't done this in a while to be honest.  Once I have those two drivers purged I can reinstall the nvidia driver, remove the amd card and then attempt to install the radeon driver properly; or I could just install the amd drivers since that card is a HD card, but I'm super not familiar with installing amd drivers.

---

### Post by StewartKMorganza on 2014-06-06
D'oh; well I felt stupid earlier.  The short version is that the slot was bad for the slot the amd was in.  The nvidia was just pretty much dead.

---

### Post by StewartKMorganza on 2014-06-06
Got the amd driver installed as well; the only problem is windows have a problem with screen tearing.  I got it working.  The closed source driver hasn't been worked on in a while and thus isn't up to date thus had screen tearing.

---

