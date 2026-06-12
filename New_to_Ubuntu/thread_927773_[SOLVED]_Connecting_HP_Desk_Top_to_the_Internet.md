---
title: "[SOLVED] Connecting HP Desk Top to the Internet"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-09-23
Good Morning, Yesterday I installed Ubuntu 7.10 on our son's computer. We are having issues getting connected to the internet. After going to historical posted events on the subject, I've tried to include some of the information here which looks appropriate.

The computer is a HP Pavilion a1610n
with: AMD 64 Duel Processor
NVIDIA Graphics
Memory: 1024 MB
HD: 250 GB
DVD Burner
------------------------------------------------------------------------
```

cole@captain-desktop:~$ sudo lshw -C network 
[sudo] password for cole: 
  *-network               
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:12:17:66:94:d1 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
cole@captain-desktop:~$ lspci -v 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        I/O behind bridge: 0000b000-0000bfff 
        Memory behind bridge: fde00000-fdefffff 
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff 
        Capabilities: <access denied> 

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
        I/O behind bridge: 00009000-00009fff 
        Memory behind bridge: fda00000-fdafffff 
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff 
        Capabilities: <access denied> 

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2) (prog-if 00 [VGA]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5 
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at e0000000 (64-bit, prefetchable) [size=256M] 
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M] 
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K] 
        Capabilities: <access denied> 

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel, IRQ 255 
        I/O ports at 4c00 [size=64] 
        I/O ports at 4c40 [size=64] 
        Capabilities: <access denied> 

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: 66MHz, fast devsel 

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16 
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16 
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
        I/O ports at f400 [size=16] 
        Capabilities: <access denied> 

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17 
        I/O ports at 09f0 [size=8] 
        I/O ports at 0bf0 [size=4] 
        I/O ports at 0970 [size=8] 
        I/O ports at 0b70 [size=4] 
        I/O ports at e000 [size=16] 
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
 
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18 
        I/O ports at 09e0 [size=8] 
        I/O ports at 0be0 [size=4] 
        I/O ports at 0960 [size=8] 
        I/O ports at 0b60 [size=4] 
        I/O ports at cc00 [size=16] 
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode]) 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=128 
        I/O behind bridge: 0000a000-0000afff 
        Memory behind bridge: fdd00000-fddfffff 
        Prefetchable memory behind bridge: fdc00000-fdcfffff 
        Capabilities: <access denied> 

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17 
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20 
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K] 
        I/O ports at c800 [size=8] 
        Capabilities: <access denied> 

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
        Flags: fast devsel 
        Capabilities: <access denied> 

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
        Flags: fast devsel 
 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
        Flags: fast devsel 

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
        Flags: fast devsel 
        Capabilities: <access denied> 

03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI]) 
        Subsystem: Hewlett-Packard Company Unknown device 2a34 
        Flags: bus master, medium devsel, latency 32, IRQ 19 
        Memory at fddff000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 

03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem 
        Subsystem: Conexant Unknown device 200c 
        Flags: bus master, medium devsel, latency 32, IRQ 255 
        Memory at fdde0000 (32-bit, non-prefetchable) [size=64K] 
        I/O ports at ac00 [size=8] 
        Capabilities: <access denied> 

cole@captain-desktop:~$ lspci -v 
```
------------------------------------------------------------------------

I'm not sure what information is needed or where to access it. I thought this would be a good place to start.

---

### Post by CoCoKnots on 2008-09-23
Please Help... I don't know that much about Ubuntu. I've tried to give what information that might be helpful. I'm kind of lost on this.:confused:

---

### Post by SarahMarieNC2 on 2008-09-23
> **CoCoKnots said:**
> Please Help... I don't know that much about Ubuntu. I've tried to give what information that might be helpful. I'm kind of lost on this.:confused:

I wish I could help. I'm new to Ubuntu as well. I will say though that all my "trying" messed me up. I did a clean install and now my card works. NO configuration was needed on my part. 

I have an HP with a linksys wireless card. I'm sure the process will be different for you. I hope that someone will be able to help you here. I am sure someone can. IT may take a day or a few days. Just keep checking back. 

Best of luck. Welcome to Ubuntu. I hope it suits you well.

Sarah

---

### Post by CoCoKnots on 2008-09-23
Thanks Sarah, I'm looking forward to this working. I appreciate the feedback... I'll keep checking as you suggest.

---

### Post by waspbr on 2008-09-23
k, first things first, what kind of connection are you trying to set up, wired or wireless

all in all, if you could perhaps post the results of

```
ifconfig
```

---

### Post by CoCoKnots on 2008-09-23
Wireless with Linksys -G...

cole@captain-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:28:CA:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3568 (3.4 KB)  TX bytes:3568 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:66:94:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4031 (3.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-66-94-D1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

cole@captain-desktop:~$ 

Thanks for the reply...

---

### Post by superprash2003 on 2008-09-23
are you trying to connect via wired or wireless? in your terminal type iwconfig and post output?? what is the exact problem you are facing?? any errors etc ?

---

### Post by waspbr on 2008-09-23
the good news here is that your wireless card already seems to be running, it doesn't need to be installed. 

from the little that I know, I reckon that inputting into terminal 

```
sudo ifconfig wlan0 up
```

should wake it up, 

then u can check if the computer is listening to any networks by doing 

```
iwlist scanning
```

this should print a list of available networks

from then you should be able to left click into the network manager applet on the top right of your screen and a list of networks should show up. 

the you just have to configure the security settings of your network and you should be done. 

weird that I could not see your wireless card in the "lspci", what kind of adapter is that, pci card? usb adapter?

---

### Post by CoCoKnots on 2008-09-23
Hi Waspbr, I would like to thank you again. You were a lot of help yesterday while I was working to install Ubuntu on my son's computer. I had to install from the CD in safe mode to get past the time zone page... That worked great. However, because of how I had installed Ubuntu, could that have anything to do with connecting to the internet ?

---

### Post by CoCoKnots on 2008-09-23
Tried that... All I received was 'Interface doesn't support scanning'...
No Scan Results

---

### Post by CoCoKnots on 2008-09-23
Sorry, The wirless connection is with a Linksys USB port wireless network adapter.

---

### Post by waspbr on 2008-09-23
no problem, I got a lot of help when I was starting so I am just passing it forward. 

anyway, the installation method is the same, the compatibility mode  doesn't change anything really just makes it lower the settings of the livecd session.So no worries there. 

k, could you input this in terminal and post the results

 ```
lsusb
```

---

### Post by CoCoKnots on 2008-09-23
cole@captain-desktop:~$ lsusb 
Bus 002 Device 004: ID 13b1:000d Linksys 
Bus 002 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 046d:08d9 Logitech, Inc. 
Bus 001 Device 006: ID 03f0:1504 Hewlett-Packard DeskJet 920c 
Bus 001 Device 001: ID 0000:0000  
cole@captain-desktop:~$

---

### Post by Joeb454 on 2008-09-23
CoCoKnots - you can paste the output of terminal commands into [noparse]```
 
```[/noparse] tags to make it easier to read :)

Also, while it may not be the best solution, have you tried an Ubuntu 8.04 Live CD to see if the wireless works on that?

---

### Post by CoCoKnots on 2008-09-23
Hi Joe... I'm not sure what you mean about the [code][code] thing... I would be glad to if I understood. also, I can't update to 8.04 without the CD... I still don't have an internet connection to do other wise.

---

### Post by CoCoKnots on 2008-09-23
Waspbr, Were you able to see anything in the lsusb information ?

---

### Post by waspbr on 2008-09-23
k,from the post above, are you using ubuntu 7.10? 

From what you told me I am assuming that the adapter that you have is this one.

[IMG]http://reviews.cnet.com/sc/32044704-2-200-0.gif[/IMG]

namely the wusb54gsc

if that's the one, than I got good news and bad news

I did some quick research and this usb is not natively supported by gutsy's or hardy's current kernel. So unfortunately you need to install the drivers, even though your computer seems to detect it, it does not work properly without the drivers.

the good news is that the next edition of ubuntu is going to support it out of the box.

now to the drivers, there is a thread about this adapter here
[http://ubuntuforums.org/showthread.php?t=225206]("http://ubuntuforums.org/showthread.php?t=225206")

the process is lengthy but very well detailed .

At the last page of the thread someone posted an alternative shorter method [http://ubuntuforums.org/showpost.php?p=5761213&postcount=303]("http://ubuntuforums.org/showpost.php?p=5761213&postcount=303")

though the first step is still required for both methods.

I myself use of those usb adapters, namely a d-link  DWL-g122 it works out of the box since gutsy. 

[IMG]http://img.epinions.com/images/opti/90/a3/pr-D-Link_DWL-G122_USB_2_0_Network_Adapter-resized200.jpg[/IMG]

they are rather unexpensive so if u don't wanna go through the methods above.

what joe meant was that you can enclose text output in cold format by pressing the **#** on the editing menu.

---

### Post by CoCoKnots on 2008-09-23
I'm using says it is the WUSB54G, but it doesn't look anything like a 'Thumb Drive'. It's more small rectangular cube with an antenna on the back. 2.4 GHz - 802.11g which connects to a USB port with a cable & stands alone.

---

### Post by waspbr on 2008-09-23
k, I did another quick search and it landed me at this thread

[http://ubuntuforums.org/showthread.php?t=192588&page=14]("http://ubuntuforums.org/showthread.php?t=192588&page=14")

I took a look at wienman's posts which lead me at this howto

[http://ubuntuforums.org/showthread.php?t=563547]("http://ubuntuforums.org/showthread.php?t=563547")

my advice would be to read up wieman's post from the first link and then follow his instructions from the second link.

Also it is always better to use the latest version, hardy's (8.04) kernel has more hardware support than gusty's (7.10)

good luck

---

### Post by CoCoKnots on 2008-09-24
OK... I'm Back. Sorry, I had to get out of here for a while. Felt like my eyes were falling out after two days of this. Something I do not understand is, this morning I tried plugging the  'Wired Ethernet (eth0)' and the internet came up without issue, complete with correct address format. Why will this not work with wireless ???

---

