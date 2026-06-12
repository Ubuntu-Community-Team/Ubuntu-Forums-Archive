---
title: "Ubuntu installation failure killed my PC!"
date: 2016-07-07
forum: New to Ubuntu
---

### Post by vbikerider on 2016-07-07
Hello.
Today I decided to delve into the world of Ubuntu and attempted to install the operating system and to my chagrin it failed, disastrously.  
On installation (it was a clean install) towards the end of the procedure it came up with a failure of the 'Boot Strapper' (or something similar, I'm new to all these terms) then it crashed my PC. Now my PC is dead.
I attempted to install the OS again but now my computer will not even see the USB ports! I do not have a disc drive (well I do have an external one but, naturally, it is a USB one!) so I cannot try to install from a disc.
I guess it is something in the BIOS or something but that is an area I have very little knowledge in.
Now I have a big dead weight sitting in the room.

The computer is rather old, it has the following bits.

EVGA nForce 680i SLI Motherboard
MSI Twin Frozer 560TI GPU
2GB DDR2 OCZ PC2 6400 Reaper Edition RAM
Intel Core 2 Quad Processor Q6700 CPU
2 x Western Digital Raptor 150GB Hard Discs in Raid 0 configuration.

The computer was working fine before the attempted installation, it was operating just before I decided to go for broke and ditch Windows! 
Woe is me...

Can anyone offer some advice as to rectifying this predicament.

---

### Post by vbikerider on 2016-07-08
Hello Myself (I guess)

I think I've managed to rectify my own fault (Thanks me!). 
I cycled to a friends and picked up an internal DVD drive and installed it into my PC and ran an old recovery disc for windows that he had for his Dell laptop.
The disc drive read the disc and must have installed some drivers (or something) and the USB ports became active.
I cancelled the install and then proceeded to install my own copy of Windows 7 from a USB stick and presto the computer is working again.

Now... do I dare to try to install Ubuntu again? If I do it might have to be side loaded for now to ensure the freshly downloaded copy of the OS installs correctly...

Cheerio.

---

### Post by mastablasta on 2016-07-08
> **vbikerider said:**
> 
2 x Western Digital Raptor 150GB Hard Discs in Raid 0 configuration.


Aside from just asking for trouble with RAID0 setup... what kind of RAID is it? hardware RAID or "Fake raid"? if "Fake raid" then forget about getting it working on Ubuntu as this is a windows thing and should be turned off in BIOS before installing Ubuntu.

from wikipedia:
> **Firmware- and driver-based[[edit]("https://en.wikipedia.org/w/index.php?title=RAID&action=edit&section=8")]**

Software-implemented RAID is not always compatible with the system's boot process, and it is generally impractical for desktop versions of Windows. However, hardware RAID controllers are expensive and proprietary. To fill this gap, inexpensive "RAID controllers" were introduced that do not contain a dedicated RAID controller chip, but simply a standard drive controller chip with proprietary firmware and drivers. During early bootup, the RAID is implemented by the firmware and, once the operating system has been more completely loaded, the drivers take over control. Consequently, such controllers may not work when driver support is not available for the host operating system.[SUP][[SIZE=2][59][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-59")[/SUP] An example is [Intel Matrix RAID]("https://en.wikipedia.org/wiki/Intel_Matrix_RAID"), implemented on many consumer-level motherboards.[SUP][[SIZE=2][60][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-60")[/SUP][SUP][[SIZE=2][61][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-RusselCrawford2011-61")[/SUP]
Because some minimal hardware support is involved, this implementation approach is also called "hardware-assisted software RAID",[SUP][[SIZE=2][62][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-62")[/SUP][SUP][[SIZE=2][63][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-KrutzConley2007-63")[/SUP][SUP][[SIZE=2][64][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-AdaptecWP-64")[/SUP] "hybrid model" RAID,[SUP][[SIZE=2][64][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-AdaptecWP-64")[/SUP] or even "fake RAID".[SUP][[SIZE=2][65][/SIZE]]("https://en.wikipedia.org/wiki/RAID#cite_note-Smith2010-65")[/SUP] If RAID 5 is supported, the hardware may provide a hardware XOR accelerator. An advantage of this model over the pure software RAID is that&#8212;if using a redundancy mode&#8212;the boot drive is protected from failure (due to the firmware) during the boot process even before the operating systems drivers take over


i am guessing you plan on doing Ubuntu only install?!

FYI - Ubuntu doens't touch BIOS during install. however if BIOS is wrongly configured or uses some windows only fucntions Ubutnu might missbehave.

> **vbikerider said:**
> 
Now... do I dare to try to install Ubuntu again? If I do it might have to be side loaded for now to ensure the freshly downloaded copy of the OS installs correctly....

complicating matters even further.

Turn off RAID, install Ubuntu (if you want to run it in RAID use mdadm  - in which case use the net install image or server image: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by giga+bytes on 2016-07-17
Definitely make sure the BIOS is properly configured to be Ubuntu friendly. I just went through a day of frustration that turned out to be because I didn't disable secure boot before installing Ubuntu (thought I did, but apparently not).

---

### Post by RobGoss on 2016-07-18
Hello and welcome, Installing Ubuntu as the only operating system should be the easiest way to go, as long as you follow the installation guide [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) -It gets complicated when you don't have a understanding how things work

Some machines may requires different configurations with in the **BIOS** settings depending on that machine, pay attention to your specs and make sure you have the correct BIOS setup. Installing _**Ubuntu will not change anything in your BIOS**_ what so ever it can only change if you've made the changes your self

---

