---
title: "Wifi Card suddenly disappears!"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by tfredj on 2011-10-09
Here's my question, short and sweet: 

    My Dell mini 9 no longer detects my wifi card. No matter which of several gnu/linux distros I'm running (several ubuntii, and others), the card no longer shows up with <lshw> or <lspci>. It's quite possible I have corrupted some necessary file somewhere (maybe even the initrd or kernel). What do I do? 

When I search for info on 'wifi card undetected', I mostly get general wifi-setup discussions (which I've much read), which routinely tell you to first check if your card is detected, but rarely say what to do if the answer is "No". So I think my question has less to do with wifi, and is more a basic pci/hardware issue - "Why no card detection?" 

If you need specific information, please be on target - say, 'the contents of the /proc/bus/pci/devices file', not 'the result of lsmod | grep -e b43' (again, this might not be a wifi issue).

---

### Post by grahammechanical on 2011-10-09
A wild guess. Can you switch WiFi off and on by pressing a few keys on the keyboard? If so, then may be that one of those keys is faulty and not allowing the wireless adapter to be switched on.

Regards.

---

### Post by gandaran on 2011-10-10
or check in BIOS if the card is disabled.

---

