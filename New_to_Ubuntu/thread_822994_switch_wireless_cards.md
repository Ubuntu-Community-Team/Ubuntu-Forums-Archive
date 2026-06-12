---
title: "switch wireless cards"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by cartisdm on 2008-06-08
I'm a victim of the 3945 wireless problems during the Hardy upgrade.  I've decided I want to just deal with it until a "real" fix comes out.  I have a USB linksys wireless card that I'm going to use.  I just did a fresh install of Hardy and now I can't figure out how to get my computer to use the USB instead of the internal 3945 card

---

### Post by tribaal on 2008-06-08
What problem are you referring to? I have a 3945 Intel chip and it works flawlessly...

Does this bug you mention have a launchpad entry? I'd be interested in helping out with it.

- Trib'

---

### Post by cartisdm on 2008-06-08
> **tribaal said:**
> What problem are you referring to? I have a 3945 Intel chip and it works flawlessly...

Does this bug you mention have a launchpad entry? I'd be interested in helping out with it.

- Trib'

[this one]("http://embeemb.blogspot.com/2008/05/wifi-on-hardy-heron-iwl3945.html") and here's some [some more about it]("http://ubuntuforums.org/showthread.php?t=765647")

I can see wireless networks, then I can even connect to them (with confirmed connection) but I can't actually access anything online.

---

### Post by quelx on 2008-06-08
Does your laptop have a hardware switch for the Intel card?  Power down and flip the switch to the off position and fire it back up.  Ubuntu (specifically nm-applet and its cronies) should pick up the new interface, if it doesn't require **ndiswrapper** or some such.

---

### Post by cartisdm on 2008-06-08
> **quelx said:**
> Does your laptop have a hardware switch for the Intel card?  Power down and flip the switch to the off position and fire it back up.  Ubuntu (specifically nm-applet and its cronies) should pick up the new interface, if it doesn't require **ndiswrapper** or some such.

Nope, no hard switch on my laptop.  I've used this card on another linux (puppy linux) laptop so I'm assuming it should work pretty well

---

### Post by quelx on 2008-06-08
> **cartisdm said:**
> Nope, no hard switch on my laptop.  I've used this card on another linux (puppy linux) laptop so I'm assuming it should work pretty well

add ```
blacklist iwl3945
``` to */etc/modprobe.d/blacklist* , reboot

---

