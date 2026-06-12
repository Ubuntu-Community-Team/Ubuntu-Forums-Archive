---
title: "bcm4318 on Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Gerinych on 2008-04-26
Hi, I just got Hardy on my computer. After a few hours of setup, I figured I need to do something with the internet. The thing is, I don't know how. I tried following some tutorials I found here, but nothing. Can you please help me?
I have a Linksys WMP54GS ver4, but on Ubuntu, it shows up as bcm4318. Weirdest thing is that it doesn't show up in Restricted Drivers. It did one time, but when I tried installing it, the computer froze, I had to press reset, then it couldn't pass ScanDisk at the startup, so I reinstalled it. Now there's no sign of it in Restricted Drivers. I read somewhere that all it takes is to pop the Ubuntu CD in, and enable the thing in Restricted Drivers, but obviously, I can't do it now.

---

### Post by Michael.Godawski on 2008-04-26
Can you please post the output of these terminal commands:

```
lspci

sudo lshw -C network

iwconfig
```

---

### Post by Gerinych on 2008-04-26
I don't know if I did this right, I typed the commands one by one because I don't know how to do that in a bunch.
```
gerinych@gerinych-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
gerinych@gerinych-desktop:~$ sudo lshw -C network
[sudo] password for gerinych: 
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:04:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:57:de:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
gerinych@gerinych-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"wildife"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
Also I did that in a normal terminal, not root, hence this is why he asked for my password.

---

### Post by unMourned on 2008-04-26
I've got about 3-5 years as Windows and Unix/AIX sysadmin experience--on top of Windows experience beginning in 1993.

I wanted to try out Ubuntu and installed on top of / beside my WinXP O/S.  See sig below:  HP zd8000's bcm4318 wireless will not play nicely with Hardy Heron for me, either.

I've tried several techniques and am thinking of scrapping it, in case my attempts stepped all over each other.

I'll have more time for this after completing graduate school next week.

-Paul

---

### Post by Gerinych on 2008-04-26
Sorry to bump, but I think there's another way to solving this. When I have Ubuntu 7.10 on another computer, it had another network card: Broadcom 4306. The way I fixed Internet on that one is I used one of the fwcutters to get the firmware out of wl_apsta.o I found on the Internet. Then I placed the files somewhere in the /lib/firmware directory in the folder bcm43xx, I think. After rebooting, it worked normally, although I had to reboot every time after changing the wireless networks in range. Is there any way I can do the same on Hardy?

---

