---
title: "sound problem"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by iyaduncc on 2008-11-18
can someone help me... i cant hear nothing on my ubuntu 8.10.....
i am a begginer in ubuntu...can someone help?

---

### Post by Crafty Kisses on 2008-11-18
What are the results of this command?
```
lspci
```

---

### Post by iyaduncc on 2008-11-18
thanks for ur help....here are the results

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by Crafty Kisses on 2008-11-18
Try the following:
```
alsamixer
```
Mess with all the volumes and what not.

---

### Post by iyaduncc on 2008-11-18
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Realtek ALC268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;                       &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;                        &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100   100<>100  100<>100  81<>81  100<>100    0<>0                       &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Mic Boos  IEC958  IEC958 D  

sorry for late reply

---

### Post by iyaduncc on 2008-11-18
they are all unmuted and all the way up but still the same....no sound effects...or nothing

---

### Post by Crafty Kisses on 2008-11-18
Have you tried installing the following package?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by iyaduncc on 2008-11-18
am installing it now...i guess its gonna take some time.....
i did not install it before...

---

### Post by iyaduncc on 2008-11-18
k

---

### Post by Crafty Kisses on 2008-11-18
You just need to accept it.

---

### Post by Moondoggy on 2008-11-18
When I installed Ubuntu 8.04 I had audio but after upgrading to 8.10 I did not so I'm quite interested in the this thread.  In my case I'm got an old Compaq EN 550.  When I run Lspci it doesn't list a sound card but when I ran ALSAMixer it says that the Card and Chip are ESS AudioDriver ES1869.  Someone on another forum suggested that I needed to run something called ALSACONF but I cannot fine this utility on my 8.04 install (I back leveled my system) and/or I'm too much of a newbie to know where to find this utility and/or how to execute.  Any help would be appreciated.  Also the steps that are being suggested followed in this thread....Would they also work for me if I were to attempt to upgrade to 8.10 again?

---

### Post by iyaduncc on 2008-11-18
sorry, it might sound funny to you but i can only read...there is nothing i can accept on that screen..

---

### Post by Crafty Kisses on 2008-11-18
What happens if you press enter?

---

### Post by iyaduncc on 2008-11-18
stays the same.....i can see its an agreement screen but the thing is that i cant accept or reject nothing....

---

### Post by iyaduncc on 2008-11-18
i just accepted it....what should i do now...

---

### Post by Crafty Kisses on 2008-11-18
Press down, then enter.

---

### Post by iyaduncc on 2008-11-18
and then!!!

---

### Post by iyaduncc on 2008-11-18
can i get some help with the sound on my hp laptob....cant hear nothing

---

### Post by Moondoggy on 2008-11-18
I was following this thead and was wondering what happened.  When I upgraded to 8.10 from 8.04 I lost my sound that was working perfectly in 8.04.  I backleveled my PC back to 8.04 and I've been trying to figure out what to do (or what I might have done wrong) when I upgraded before trying again.  So far, it looks like others are having the same isssue when upgrading so I'm not sure what the deal is.  Any thoughts?

---

### Post by SuperSonic4 on 2008-11-18
Have you checked if the headphones are plugged into the green audio socket

---

### Post by Moondoggy on 2008-11-18
Well....I'm not that much of a newbie....The system is an older Compaq EN 550 tower that has a built in speaker that is enabled all the time by default.  Here's the story from the beginning.....

I used a CD to install 8.04 and after the install the system worked flawlessly.  After 8.10 came out I opted to upgrade but afterwards, no audio.  I didn't have time when that all happened to figure out what I needed to do so I simply reinstalled 8.04 from the CD again and like magic, everything is working flawlessly again so I'm wondering if I should attempt another upgrade of stick with 8.04.  I will tell you the following....I ran LSPCI -VV on my system and it does not show a sound card however in several locations within 8.04 I've been able to identify the card/chip thru ALSAMixer as and ESS AudioDriver ES1869 and Compaq lists an ES1969 driver on their website for Windows NT that was origionally installed on the machine.

So...I've read a post on another forum with this site and it appears that the loss of Audio is more common than I had imagined and at this point I'm a bit lost as to my next step.  On another web site someone told me to save my configuration files, export my package database and reinstall but for a newbie this is all greek to me since I don't have a clue how to do any of the above or whether this is a better technique then upgrading and trying to fix the sound problem.  

Any help/direction would be appreciated.

---

