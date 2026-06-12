---
title: "Belkin Wireless not registering"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by Mobius1995 on 2012-03-01
I recently installed ubuntu onto my computer; however, according to the forum rules, I'm an absolute "green" user. I have no experience with it whatsoever, and moved simply because Windows Vista annoys me for some reason. On vista, I am able to receive wireless via my Belkin N300, model: F7D2102. On ubuntu (which is on the same computer), I am unable to locate any wireless networks, and when I attempted to re-install it with the Disk that came with it, it simply will not work. Any suggestions? Help is much appreciated.

---

### Post by Lokireloaded on 2012-03-01
Can you put your terminal ouput to 

```
lspci
```and 

```
ifconfig
```

---

### Post by Mobius1995 on 2012-03-01
**_output for lspci_**:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

**_output for ifconfig:_** 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:830_****_

---

### Post by Lokireloaded on 2012-03-01
Well I'm 99% certain that the router is not at fault. I say that as there could be a problem with the router.
My best guess is that it is either a driver issue or, (hopefully not) a  hardware issue.

---

### Post by Mobius1995 on 2012-03-01
Ok, thank you. Do you have any recommended course of action, or areas of study which would allow me to further investigate the problem?

---

### Post by Lokireloaded on 2012-03-02
Maybe you could try this.

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)



Sorry I couldn't be more more use.

---

