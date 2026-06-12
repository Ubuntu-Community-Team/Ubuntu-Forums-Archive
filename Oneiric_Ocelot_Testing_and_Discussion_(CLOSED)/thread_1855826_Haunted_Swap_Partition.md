---
title: "Haunted Swap Partition?"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 4Orbs on 2011-10-07
Is it possible for a previous installation to leave remnants in the swap partition that can affect the behavior of a new installation somehow?

---

### Post by meborc on 2011-10-07
i highly doubt it. If installing from alternate cd, the installer automatically selects SWAP partition to be formated as well (after selecting the partitions and mount points, you get the verification screen and swap has always been set to be formated on my machines automatically)

Now the live-cd installation does not show it, but I believe it does it "behind the scenes" anyway. And you always have the option to format the swap partition while installing a new system

---

### Post by ronacc on 2011-10-07
I have a multi-drive multi-boot multi-install/distro box and a new install always finds and uses ALL swap partitions on all drives for all distros and this has never caused me a problem , however I don't know if any of my disto's / installs have actualy ever written anything to swap I have 4 gig mem and don't recall seeing swap showing usage .

---

### Post by alexvy13 on 2011-10-07
I've had it just create extra swap partitions when reinstalling, but I too, have never seen it used.  Would it be safe to just delete the partition?

---

### Post by ronacc on 2011-10-07
as long as you have pleanty of memory its safe , I run with no swap on my early eeepc that only has a 4gb ssd but i've got 2gb mem stuffed into it and keep multitasking to minimum to avoid maxing it out and needing swap , swap is mainly needed for older systems with limited mem .

---

### Post by SirDrexl on 2011-10-07
I don't think it could be haunted unless you use Norton Ghost.  ;)

---

### Post by dFlyer on 2011-10-07
I don't believe anything from swap can cross over as swap is dumped on each boot.

---

### Post by 4Orbs on 2011-10-07
Thanks for the answers, folks. Your replies pretty-much reflect what I have taken for granted during the past three years.

But this is why I asked... I had been using Mint-Debian for several days and had wine installed from the unstable repo. Wine behaved strangely, but worked well enough. Then I replaced the mint install with Ubuntu 11.10, and after installing wine on Ubuntu... it behaved in the same odd way as it had on Mint-Debian. I just assumed there were still some bugs to be worked out in the Ubuntu repo version. Then I played a hi-def movie with vlc which wrote an unusually large amount to swap (memory leak?). And following that event... wine seemed to suddenly fix itself and behave as I expected it should in Ubuntu. Swap appears to be the only thing to which I can attribute the wine self-healing. I hadn't done any recent updates or modifications. FWIW, all is working well now. Thanks again for your replies.

---

### Post by VinDSL on 2011-10-09
> **ronacc said:**
> swap is mainly needed for older systems with limited mem [...]
Heh!  That would be my system.  :D

For the sake of discussion...


To dump your swap partition(s):
```
sudo swapoff -a
```

To restart the swap partition(s):
```
sudo swapon -a
```


This comes in handy, sometimes, saving the hassle of having to perform a restart/boot. ;)

---

