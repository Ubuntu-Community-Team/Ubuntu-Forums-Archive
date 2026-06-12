---
title: "[SOLVED] Wireless Connection Issue, Ubuntu 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by REIGN SS on 2008-11-03
I'm having an issue getting my wireless to work using Ubuntu 8.10 AMD64.

I'm Dual Booting 8.10/M$ Vista. I'm using a Netgear WG111v2 USB wireless adapter.

I'm having a bit of a "strange issue"; my adapter installs, and will find/connect to my wireless network but when I try to browse to a webpage, or DL updates nothing happens and I get Offline/Cannot connect messages.

From the searching I've done most people ask for the following commands:

**iwconfig:**
```

ryan@ryan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:A2:D3:EA   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=24/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

**lspci:**
```

ryan@ryan:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)


```

**lsusb:**
```

ryan@ryan:~$ lsusb
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks in advance for any help you can offer.

---

### Post by REIGN SS on 2008-11-03
Anyone please?

---

### Post by LowSky on 2008-11-03
Have you tried rebooting the wireless router?

otherwise try this
[http://ubuntuforums.org/showthread.php?t=51993](http://ubuntuforums.org/showthread.php?t=51993)

---

### Post by LowSky on 2008-11-03
EDIT double post

---

### Post by REIGN SS on 2008-11-03
Well, I installed the i386 version of Ubuntu 8.10 used NDISwrapper but instead of the WindowsXP driver I had to use the Windows 98 version. Seems to be working now

WOOT!

I guess this is solved"ish".

---

