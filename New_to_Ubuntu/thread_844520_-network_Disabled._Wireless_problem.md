---
title: "*-network Disabled. Wireless problem"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by _AcNovember on 2008-06-29
I`ve just installed Ubuntu 7.10 again on my laptop. HP G5000.
Everything works nicely, except for the wireless, I`ve googled and forum searched some and found a troubleshoot comand "Sudo lshw"
looking for the card, and this came up:

configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth1
                version: 01
                serial: 00:1a:73:1f:13:2a
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


Now, logic tells me that the card has been disabled, but I havent found any thing on both this or the norwegian forum (Or google) that could help me. Also I`m new on linux.
Help me anyone?

---

### Post by _AcNovember on 2008-06-29
Currently updating and stuff, So I have a vague hope that it will fix itself with the updating. Very vague, tho.

---

### Post by MeeMaw on 2008-06-29
> **_AcNovember said:**
> Currently updating and stuff, So I have a vague hope that it will fix itself with the updating. Very vague, tho.

So if you are updating, do you have a wired connection? If so, they won't both work at the same time. To get your wireless to work, the wired connection has to be disconnected. Then try to configure using this 
[https://help.ubuntu.com/](https://help.ubuntu.com/)
or this
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

I'm sure you'll get it going!
:)

---

### Post by _AcNovember on 2008-06-29
Yeah I have wired connection now, but before I was forum lurking and googling on another laptop while trying out stuff on this one. I know they wont both work at the same time :P The problem is not that, the problem is that the wireles card is just not playing nice with linux. :/

 I`ll try the links as the updates finish, thank you!

---

### Post by st33med on 2008-06-29
Try this link: [http://ubuntuforums.org/showthread.php?t=760568]("http://ubuntuforums.org/showthread.php?t=760568")

---

### Post by _AcNovember on 2008-06-29
> **st33med said:**
> Try this link: [http://ubuntuforums.org/showthread.php?t=760568]("http://ubuntuforums.org/showthread.php?t=760568")
Ah, thank you, It says it will not work unless I have Hardy (guessing that is the upgraded version im getting now) So I`ll try it after that :D

---

### Post by _AcNovember on 2008-06-29
Currently typing on wireless network. :D Thanks for the tips

---

