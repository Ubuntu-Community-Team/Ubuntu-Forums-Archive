---
title: "Help me please to find the following on my computer:"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Gost-Taras on 2008-09-14
Guys i received home work from my it class and all it is i need to find the following things on my computer, how can i do that ? i use only Ubuntu 8.04 Thank you

Hardware
Motherboard
Northbridge
Southbridge
Bios
CPU
RAM
Hard drive
Sound card
Network card
Ports/connectors 
IDE
PCI
PCIe
SATA
USB
Firewire
PS2
Serial 
parallel

---

### Post by niccholaspage on 2008-09-14
Open a terminal.Type this:
```

sudo apt-get install hwinfo
hwinfo --short

```
You may remove the --short command though this will give a lot more info.

---

### Post by bobnutfield on 2008-09-14
The following will put a detailed list of hardware on your desktop that you can open with a web browser:

> sudo lshw -html > ~/Desktop/hardwareinfo.html

---

### Post by Oldsoldier2003 on 2008-09-14
From the CoC
> 6. While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

I am using my discretion as a moderator and leaving this thread as a reminder that Asking for homeowrk answers is not allowed on this forum.

---

