---
title: "network connection bug"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Stargazer989 on 2008-09-11
when i load from hibernate i have no network connection, any ideas ?

---

### Post by Zzl1xndd on 2008-09-11
There are some ACPI issues with a number of notebooks that I have seen. Could you tell us the make and model as someone might have dealt with your problem before.

My notebook has this problem with its wireless card and the only way I have been able to get it to come back is using the physical  switch on it to turn it off then on again.

---

### Post by Stargazer989 on 2008-09-11
actually this is a desktop... eMachines T5224, with a wired connection, Cable.
A restart from System > Quit... works fine. i just have like 3 or 4 programs open that i don't like restarting.

---

### Post by DFlame on 2008-09-11
I'm unsure if I can solve the problem, but more information could be helpful.

Is this a wired or wireless connection? If wireless, what drivers are you using? (eg: b43, ndiswrapper, madwifi)

The model of your hardware can help too. An output of lspci in terminal should show this.

Finally, what version of Ubuntu are you running?

Cheers,

DFlame

---

### Post by Stargazer989 on 2008-09-11
> **DFlame said:**
> I'm unsure if I can solve the problem, but more information could be helpful.

Is this a wired or wireless connection? If wireless, what drivers are you using? (eg: b43, ndiswrapper, madwifi)

The model of your hardware can help too. An output of lspci in terminal should show this.

Finally, what version of Ubuntu are you running?

Cheers,

DFlame
i did say it is a cable connection... wired...
lspci results:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:01.0 Communication controller: Conexant Unknown device 2f40
06:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
```

and finally: ubuntu 8.04 hardy heron

---

### Post by Stargazer989 on 2008-09-25
it's still happening though it's an on/off thing :|

---

