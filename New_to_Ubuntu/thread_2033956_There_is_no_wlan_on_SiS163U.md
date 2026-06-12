---
title: "There is no wlan on SiS163U"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by sgtGiggsy on 2012-07-27
Hi.

I rather new to Ubuntu. I tried it on my desktop PC, and it's worked like a charm, so when I bought a used laptop (Dell D520) I decided to install Ubuntu as main OS on it. Everything is fine, except I can't get my wlan work. It's Fujitsu Siemens SiS163U, and it was installed in the laptop, when I bought it. With Win7, the wlan works without any problem, but under Ubuntu (12.04) I can't make it work.
I installed ndiswrapper, and I tried all available versions of Windows drivers with it, but none of them worked as it should. With Win98, and Win NT driver, I was able to make it see the wlan card (when I enter the terminal the "iwconfig wlan0" command it lists every detail about the wlan card), but when I turn on the wi-fi with its hardware key, the OS stops working. It just freezes, and not doing anything. The same thing when I try to start the system with wi-fi turned on, it doesn't start at all, stops before the logon screen appears. Without wi-fi, everything is fine. What could cause this? I would appriciate any help you can provide me. Thank you.

---

### Post by mapes12 on 2012-07-27
I guess this is your best bet:-

[http://w3.sis.com/download/download_step1.php](http://w3.sis.com/download/download_step1.php)

other than that you may need to get hold of an alternative Linux supported wifi adapter.

---

### Post by kurt18947 on 2012-07-27
A good start might be to post the output of the command typed in a terminal:
```

lspci

```

It should look something like this:

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)
02:06.0 USB controller: NEC Corporation USB (rev 43)
02:06.1 USB controller: NEC Corporation USB (rev 43)
02:06.2 USB controller: NEC Corporation USB 2.0 (rev 04)

---

### Post by sgtGiggsy on 2012-07-27
Thank you, but it still doesn't work. So is it some hardware related crash, what can't be solved? Is it possible wi-fi would work on some other Linux distribution, or if it isn't work on Ubuntu, neither on the others?

---

### Post by sgtGiggsy on 2012-07-27
> **kurt18947 said:**
> A good start might be to post the output of the command typed in a terminal:
```

lspci

```

It should look something like this:

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)
02:06.0 USB controller: NEC Corporation USB (rev 43)
02:06.1 USB controller: NEC Corporation USB (rev 43)
02:06.2 USB controller: NEC Corporation USB 2.0 (rev 04)


I got this, when I entered lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
```

So I don't see any info about the wlan card here. I got the same with the driver installed, and without it. On the other hand, with the
```
iwconfig wlan0
```
command, there is a difference. With the driver installed it says:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:18 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

When the driver isn't installed, it says:
```
wlan0     No such device
```

So it's rather odd.

---

### Post by kurt18947 on 2012-07-27
Maybe try 'lsusb?'.  If the adapter doesn't show up with of those commands,  it ain't gonna be simple I think.  A known-to-work USB adapter might be the simplest route if you just want a functional network.  If you want to dig into the guts a bit then carry on. :)

---

