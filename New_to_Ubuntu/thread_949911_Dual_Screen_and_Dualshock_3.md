---
title: "Dual Screen and Dualshock 3"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by RasputinForever on 2008-10-16
I have two issues I'm trying to resolve...

First I'm trying to set up a dual screen situation.  I'm using a hp pavillion zv6000 which has an s-video port.  In windows I could use my television as a second screen which I used to play videos and such.  It was nice.  But I can't figure out how to do it on Ubuntu!  Last time I tried I messed up a few things and I'm reluctant to try again without some direct help.

Also!

I'm trying to use my Dualshock 3 or my Sixaxis controllers (from the ps3) on my PC.  On windows I had to install a small program, but after doing some searching all I have to do is plug it right in, right?  Well, after doing that and pressing buttons, trying to follow other people's guides (and failing) I'm just about all out of ideas.  To be specific, I would like to use my DS3 controller with zsnes.

Anyway, any help would be greatly appreciated, and yes, I am a begginer so please bear with me. 

Thank you!

---

### Post by LowSky on 2008-10-16
for the Sixxaxis/DS3 [http://ph.ubuntuforums.com/showthread.php?t=931864](http://ph.ubuntuforums.com/showthread.php?t=931864)

what kind of the graphics card on that computer? nvidia or ATI... I dont feel like looking

---

### Post by RasputinForever on 2008-10-16
> **LowSky said:**
> for the Sixxaxis/DS3 [http://ph.ubuntuforums.com/showthread.php?t=931864](http://ph.ubuntuforums.com/showthread.php?t=931864)

what kind of the graphics card on that computer? nvidia or ATI... I dont feel like looking

it is ATI

---

### Post by RasputinForever on 2008-10-17
I'm having a few persisting issues...

Firstly, Step 2.c in USB pairing [on this page](https://help.ubuntu.com/community/Sixaxis) confuses me.  I just don't understand what I'm supposed to put into the terminal at this point.

Also.  [On this page](http://ps3.jim.sh/sixaxis/usb/), there is a link to a patch which leads me to something very intimidating.  I simply don't understand.  

I feel like I can only find solutions on how to use my ps3 controller via bluetooth, when I just want the system to not just recognize, but be able to use it when plugged in via USB for something like zsnes or other silly things like that.  

Any help with either of these two things would be greatly appreciated.

---

### Post by LowSky on 2008-10-17
> **RasputinForever said:**
> it is ATI

ATI what?

run this command from terminal and post 

```
lspci
```

> Firstly, Step 2.c in USB pairing on this page confuses me. I just don't understand what I'm supposed to put into the terminal at this point.

```
sudo ./sixpair

```

---

### Post by RasputinForever on 2008-10-17
I'll run that code when I get back to my computer...

I've tried running that second bit of code and it does nothing.

---

### Post by RasputinForever on 2008-10-19
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Aha, there we are.

==

Then, on the ps3 subject, steps 2.b and 2.c I get these results... 

```
rasputin@steve-jr:~$ gcc -o sixpair /home/rasputin/sixaxis/sixpair.c -lusb
rasputin@steve-jr:~$ sudo ./sixpair
Current Bluetooth master: 00:1b:fb:97:76:81
Unable to retrieve local bd_addr from `hcitool dev`.
Please enable Bluetooth or specify an address manually.

```

Hmm, not sure what's wrong here... I did follow step 2.a and that is the correct file path for sixpair.c.  Not sure what is going on, I could be wrong!

---

### Post by RasputinForever on 2008-10-20
Any help.  Pretty please.

---

### Post by RasputinForever on 2008-10-23
Sorry, I know its annoying do this.:confused:

---

### Post by zerothis on 2011-08-20
still unsolved, i have the same issue

---

