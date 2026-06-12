---
title: "[SOLVED] Damn Small Linux Internet Problems"
date: 2007-12-12
forum: Other OS Talk
---

### Post by shadow-of-sin on 2007-12-12
Well I've installed Damn Small Linux onto a flash drive and have managed to boot into it however the internet doesn't work. My ethernet hardware is: "3com 3c920 integrated fast ethernet controller 3c905c-tx compatible". After a google search and viewing some irc logs it seems that this particular NIC is problematic in Linux. So has anyone managed to get this to work in DSL or have any clues on how to do so?

Thanks in advance,

---

### Post by tgalati4 on 2007-12-12
I've used DSL on older hardware without problems.  Two things come to mind:

1)  blacklist the currently loaded driver, then manually load it after boot, then 

> pump -i eth0  (to get an ip address)

2)  manually load the driver with optional switches.  You will have to search for viable switches.


3) (Bonus)  Turn off serial port and parallel port to free up interrupts, could be an interrupt conflict, see if ethernet card is sharing an interrupt (more /proc/interrupts).

---

### Post by shadow-of-sin on 2007-12-13
Ah, I found out what was wrong...it turns out I was using an old version of the boot floppy and the modprobe command didn't work on it (when I tried to manually load the drivers as you said). Using a new floppy everything works fine...I'm posting from DSL right now :D

Thanks for your help

---

