---
title: "rocket fish 7.1 pci problems"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by aufer on 2014-04-29
So I'm fairly new to linux I've fiddled with it to run game servers years ago but other then that not much else.
Anyway that being said.
The onboard sound for my e-machines d5239 desktop works fine.  I just disabled it in the bios in attempt to get this card to work
I purchased a rocketfish 7.1 pci model # rf-71sdcd and it ran fine when this pc was running windows.
Now that I'm on kubuntu 14.04 LTS I can't seem to get it to work.
If you reply I'd like to do everything from the command line if possible.
Please keep in mind I am new and would need you to talk to me like I'm a 5 year old.
I have read many posts about getting it to work with alsa and attempted a few walk through's on different posts to no avail.
apt-get says i have the current version of alsa-base if your curious.

here is my lspci
```
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a2)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```
From what I have read in other posts it may be detecting the card as CA0106 but i have tried using that too please baby step me on how to get this card up and running.

Let me know if you need more info from me.
Thank you in advance.

---

