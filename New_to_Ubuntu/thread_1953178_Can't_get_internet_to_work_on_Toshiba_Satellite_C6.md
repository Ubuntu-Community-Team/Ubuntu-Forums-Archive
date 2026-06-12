---
title: "Can't get internet to work on Toshiba Satellite C655"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by IEBFil on 2012-04-05
Hey, I have exhausted my knowledge to try and solve this issue. I'm using 11.04 and have no idea where to begin. So, ask what you need to know and thanks in advance for the help.

---

### Post by anewguy on 2012-04-05
The very first thing I would do, as it is what the vast majority of us do when providing help, is a google search with:

ubuntu 11.04 toshiba satellite c655 internet (or perhaps you mean wireless?)

The second thing is information we need before we can help you:

- open a terminal window and type (press enter after each line):

lspci > dwetest.txt
lsusb >> dwetest.txt
lshw -C network >> dwetest.txt
ifconfig  >> dwetest.txt
iwconfig >> dwetest.txt

Close the terminal window.

Using the GUI file explorer, copy the file "dwetest.txt" from your home folder to a flash drive (or if you dual-boot Windows, copy it to somewhere on your Windows drive).

Now you should be able to get on the internet somewhere (like where you are posting from), reply back here and attach the file to your post.

Dave ;)

---

### Post by IEBFil on 2012-04-05
Hey, thanks. This is what I got from the dwetest.txt file:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05dc:a410 Lexar Media, Inc. JumpDrive 128MB/256MB
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:5a:ef:a9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d0200000-d0203fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:cd:e6:5e
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:41 memory:d0100000-d013ffff ioport:2000(size=128)
eth0      Link encap:Ethernet  HWaddr 00:26:6c:cd:e6:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10128 (10.1 KB)  TX bytes:10128 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:5a:ef:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
And, I did mean wireless. Sorry about that, haha.

---

### Post by anewguy on 2012-04-05
I'm going to have one the networking experts come here to help you - wildmanne39.

Dave ;)

---

### Post by anewguy on 2012-04-06
Since they haven't made it over here yet, let's keep going.
Try the following:


sudo modprobe -r acer_wmi


This will hopefully be all it takes (pay no attention that it says "acer").  If your wireless starts working (until your next reboot), post back and we'll make it permanent.


If that doesn't work, then please post the output of:


lsmod


back here in a reply.  That will let us know what modules are being loaded, including the driver it thinks it should use for your wireless.


We can go from there.

Dave ;)

---

### Post by wildmanne39 on 2012-04-06
Hi, please post the output of:
```
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by anewguy on 2012-04-06
> **wildmanne39 said:**
> Hi, please post the output of:
```
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks for the help!!  You've probably noticed I don't claim to be an expert at anything, but if I dig around enough I can usually come up with something that works, but having someone who is an expert in an area makes it real handy for someone getting their answer quicker - and I get to learn something to put in the back of the ol' noggin for later! ;);)

Dave ;)

---

### Post by anewguy on 2012-04-09
OP - what is the status of this problem?

---

