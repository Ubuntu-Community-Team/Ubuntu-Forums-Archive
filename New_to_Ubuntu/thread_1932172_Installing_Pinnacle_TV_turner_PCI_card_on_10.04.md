---
title: "Installing Pinnacle TV turner PCI card on 10.04"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by lennih on 2012-02-26
Kernel: 2.6.32
when I run tvtime from a terminal I get:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/hernan/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Segmentation fault

If I run lshw, I get, among other things:


          *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: AV/DV Studio Capture Card
                vendor: Pinnacle Systems Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=16 mingnt=8
                resources: memory:ff510000-ff510fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Pinnacle Systems Inc.
                vendor: Pinnacle Systems Inc.
                physical id: 2.1
                bus info: pci@0000:06:02.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=80 mingnt=32
                resources: irq:18 memory:ff511000-ff5117ff

I've read quite a few threads, but I can't find the solution. And I tried to follow a couple of step-by-step guides, but they don't work. Thanks in advance.

---

### Post by mapes12 on 2012-02-27
Never tried it myself but running this on a Live CD may help. It could have some hardware support not in the main Ubu release:-

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by lennih on 2012-02-27
Isn't it Mythbuntu a different distro?
I'd like to be able to use the card from Ubuntu.
I'd be glad if you guys could help me with that. Rebooting to use the card, setting everything up and then back again to your OS when you've finished is not a convenient option for anyone.

---

