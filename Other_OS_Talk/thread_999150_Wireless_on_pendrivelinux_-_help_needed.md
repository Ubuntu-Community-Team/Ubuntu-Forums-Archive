---
title: "Wireless on pendrivelinux - help needed"
date: 2008-12-01
forum: Other OS Talk
---

### Post by LMD1990 on 2008-12-01
I just got Pendrivelinux 2008 on my 4GB stick today, and it works fine- but I really haven't a clue how I go about setting up the wireless internet on it. It's a Mandriva/Debian derivative that uses KDE, and I only really know GNOME, so I'm a bit lost.

Apparently, this is my wireless card:

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

I think I found the right Windows driver (Atheros_driver(5005G)) but when I try to install it via ndiswrapper on pendrivelinux, it says "unable to find the ndisrwapper interface!"

I could do with a step-by-step, minimal jargon walkthrough on how to do this, from beginning to end.

Thanks in advance guys.

EDIT: I tried installing ndiswrapper, but got an error saying that the kernel version could not be found, but I've not a clue how to fix this.

---

### Post by wolfen69 on 2008-12-01
search synaptic for madwifi and install that.

---

### Post by LMD1990 on 2008-12-02
1) I can't use synaptic because I don't have an internet connection. It doesn't even work on LAN.

2) I tried installing madwifi from a tarball and it wouldn't let me, something about a missing module or something.

I could do with being run through the process, because I'm rather new to this.

---

### Post by LMD1990 on 2008-12-02
Can anybody help? My pendrivelinux is pretty much useless without internet :(

---

