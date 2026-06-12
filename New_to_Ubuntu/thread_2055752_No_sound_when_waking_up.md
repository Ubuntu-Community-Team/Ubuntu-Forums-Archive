---
title: "No sound when waking up"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by S2UIRR3L on 2012-09-10
I have a question about sound. When I put the computer into "Suspend" mode, then "wake it up" it has no sound. If I reboot, the sound comes back.

I like the suspend mode because it doesn't turn off the computer, it just puts it to sleep and it wakes up quickly when I need to use it in a hurry lol.

The purpose is kinda sorta defeated when I have to sit there, wake it up, then go into total reboot in order to get the sound working again... right?

Everything else works. The mute boxes are all clear (not ticked). There's no video problems. There's no wireless problems... Just don't have sound.

I don't know how much this will help, but thought I'd try posting the results of "lspci" to get the ball rolling in here. If there's anything else, just ask.

```
rabidsquirrel@rabidsquirrel-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
rabidsquirrel@rabidsquirrel-laptop:~$ 

```The sticker on the bottom pannel lists it as a Gateway MA3. But when I search it, it always comes up as a Gateway MX6450. Thanks in advance!

---

### Post by S2UIRR3L on 2012-09-10
Oh, by the way... I failed to mention that I'm using 10.04 Lucid Lynx 64-bit, if that makes anything different?

---

### Post by S2UIRR3L on 2012-09-19
Bump

I still have this problem and don't know where else to look or ask for suggestions or instructions on how to "fix" this.

If I put the laptop to sleep, then I wake it up, there's no sound. I've made sure that all levels are up and aren't muted.

???

---

