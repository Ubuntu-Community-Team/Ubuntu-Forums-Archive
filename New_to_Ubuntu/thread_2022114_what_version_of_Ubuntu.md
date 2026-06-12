---
title: "what version of Ubuntu?"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by Dave.B on 2012-07-10
I have a dell D430 that has a core2duo processor.  is that processor a 64 bit processor?  what is the best version of Ubuntu to use?

---

### Post by Pilot6 on 2012-07-10
Yes, it is 64 bit. Version is a matter of taste. I suggest to start with Ubuntu 12.04.

---

### Post by GreatDanton on 2012-07-10
It depends on the amount of Ram. If you have 1Gb or less I would recommend you to stick with xubuntu or lubuntu. If you have more than 1Gb, then definitely stick with Ubuntu.

---

### Post by codingman on 2012-07-10
^+1
Again, depends on the amount of ram, and also your personal taste, if you have more than 1gb, then go for Ubuntu 12.04 or Kubuntu 12.04, if less than 1gb, go for Lubuntu or Xubuntu. Ubuntu uses the Unity desktop environment, Kubuntu uses KDE, Lubuntu uses LXDE, and Xubuntu uses XFCE, all very nice distributions.

---

### Post by codingman on 2012-07-10
My post above showed the distro's with their default DE's, Lubuntu also comes with Openbox, but I would not recommend that for new users to Linux.

---

### Post by Dave.B on 2012-07-10
i DLed the 64 bit version of Ubuntu and it says amd64.  will that work with the 64bit core2duo Intel chip?

---

### Post by PaulW2U on 2012-07-10
> **Dave.B said:**
> i DLed the 64 bit version of Ubuntu and it says amd64.  will that work with the 64bit core2duo Intel chip?

Yes it will work, don't worry about the **amd** designation.

I think amd64 refers to the _instruction_ set of the chip rather than the _maker_ of the chip. ;)

---

### Post by mlentink on 2012-07-10
yes

---

### Post by Dragonbite on 2012-07-10
> **codingman said:**
> ^+1
Again, depends on the amount of ram, and also your personal taste, if you have more than 1gb, then go for Ubuntu 12.04 or Kubuntu 12.04, if less than 1gb, go for Lubuntu or Xubuntu. Ubuntu uses the Unity desktop environment, Kubuntu uses KDE, Lubuntu uses LXDE, and Xubuntu uses XFCE, all very nice distributions.

Isn't 64bit capable of handling >3 GB of RAM while the 32bit require an extra "step" to see more than 3GB?

---

### Post by GreatDanton on 2012-07-10
True, but codingman was speaking in general, since we still don't know the amount of Ram. Edit;

---

### Post by Paqman on 2012-07-10
> **GreatDanton said:**
> 32bit version does not recognize more than 3Gb of ram.

Yes it does, the PAE kernel is the default now.

---

### Post by GreatDanton on 2012-07-10
ooops, my mistake.

---

### Post by Paqman on 2012-07-10
> **GreatDanton said:**
> ooops, my mistake.

Not to worry, it's a pretty new development.

---

### Post by Dragonbite on 2012-07-10
> **Paqman said:**
> Yes it does, the PAE kernel is the default now.

I thought there was something that allowed 32 bit to view more than 3GB. So it's now a moot point since it is included in the default kernel? That's great!

---

### Post by Paqman on 2012-07-12
> **Dragonbite said:**
> I thought there was something that allowed 32 bit to view more than 3GB.

Yep, that's PAE: Physical Address Extension. It's been available for ages, but you had to deliberately install the PAE kernel. That's now the default for 32-bit machines.

PAE is a bit of a kludge though, you should always use 64-bit if you can.

---

### Post by Dragonbite on 2012-07-12
> **Paqman said:**
> Yep, that's PAE: Physical Address Extension. It's been available for ages, but you had to deliberately install the PAE kernel. That's now the default for 32-bit machines.

PAE is a bit of a kludge though, you should always use 64-bit if you can.

Come to think of it, this was the piece that was keeping the base Ubuntu 12.04 image from booting up on my machine so I had to go to an alternate spin image without PAE enabled to install it!  I forgot about that, now that makes sense.

At least on that system, I don't have to worry about it because it can only handle up to 2 GB of RAM.

---

