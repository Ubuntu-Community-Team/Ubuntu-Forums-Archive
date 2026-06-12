---
title: "[SOLVED] Atheros 802.11 isn't quite working"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by inxygnuu on 2008-10-05
Hello, I just installed Ubuntu Intrepid and My Atheros 802.11 Wireless is not quite working. With Intrepid it does recognize it but it is still not working. Can  anyone help me?

---

### Post by inxygnuu on 2008-10-05
anyone:confused::confused::(:(

---

### Post by shifty_powers on 2008-10-05
what is the output of

```
lspci
```

```
ifconfig
```

and

```
sudo iwlist scan
```


?

---

### Post by inxygnuu on 2008-10-05
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


eth0      Link encap:Ethernet  HWaddr 00:1e:68:95:10:70  

          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::21e:68ff:fe95:1070/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:31948 errors:0 dropped:0 overruns:0 frame:0

          TX packets:18873 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:35017582 (35.0 MB)  TX bytes:3699255 (3.6 MB)

          Interrupt:220 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:3116 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3116 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:155800 (155.8 KB)  TX bytes:155800 (155.8 KB)


lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



pan0      Interface doesn't support scan

---

### Post by shifty_powers on 2008-10-05
go to system>admin>restricted drivers (iirc)

is the driver enabled?

---

### Post by inxygnuu on 2008-10-05
checked it right after I upgraded:). yes it is enabled.:)/:(

---

### Post by shifty_powers on 2008-10-05
k. have you heard of madwifi?

it is a set of drivers for the atheros chipsets.

[http://ubuntuforums.org/showthread.php?t=902860&p=5711824](http://ubuntuforums.org/showthread.php?t=902860&p=5711824)

details how to get it and use it for your card.

probably your next step :D

---

### Post by inxygnuu on 2008-10-05
Thanks dude, now can i re-enable the atheros, because the sound won't work, I mean it works for the drum sound for when you log-in to Ubuntu, but I can't watch any youtube movies...:(:(

---

### Post by shifty_powers on 2008-10-06
do you get video in flash, but no sound?

try

```
sudo apt-get install ubuntu restricted extras
```

---

### Post by inxygnuu on 2008-10-06
yeah, I can see the video but I cant hear any sound. the restricted extras wont download: "Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu"

---

### Post by inxygnuu on 2008-10-06
Oh yeah, also, it is just the Internet, i did a hardware test (up to the sound) and I could hear, so it is just the internet, if that helps...:???:

---

### Post by Dylanby on 2008-10-06
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by inxygnuu on 2008-10-06
nope, that doesn't help, my wireless isn't even working anymore.:(:(:( and I am afraid to restart my computer because the new Linux Kernel doesn't load that well. In fact I'm kinda scared!:cry::cry::cry:

---

