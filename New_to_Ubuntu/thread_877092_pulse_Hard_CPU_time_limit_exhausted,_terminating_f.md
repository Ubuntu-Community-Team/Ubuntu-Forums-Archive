---
title: "pulse: Hard CPU time limit exhausted, terminating forcibly."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by MillDaKill on 2008-08-01
My pulseaudio instance keeps dieing and this is the error message I get.  It will usually run for about 20-30 minuets before it goes down.  It seems like it is pretty random when it goes down.  I have been having this problem since I installed 8.04 a few months ago.

Soft CPU time limit exhausted, terminating.
Hard CPU time limit exhausted, terminating forcibly.
Aborted


I am running Ubuntu 8.04 64bit. Here is my lspci output.
comp@computer:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

---

### Post by vikramaditya on 2008-08-01
As so many here say, try using ALSA instead of Pulse.  I've personally had no trouble with Pulse, but it seems the problem most often manifests on laptops with somewhat marginal hardware specs.  Then again, I may be full of ****. :)

---

### Post by tisk on 2009-02-14
Please contribute to this bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/279847](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/279847)

---

