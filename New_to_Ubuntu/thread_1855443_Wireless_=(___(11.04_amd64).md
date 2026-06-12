---
title: "Wireless =(   (11.04 amd64)"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Tjkent on 2011-10-06
Below is my lspci output.  I am having trouble using my wireless card, and to use ethernet, I have to go through a series of steps every time I log on, please help me.


00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9641
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 170a
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

---

### Post by amjjawad on 2011-10-06
Hello and Welcome :)

Please run this command:

```
 sudo lshw -C network
```

and post the output here but please make sure to wrap up the text with "CODE" tags.
[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

Thanks!

---

### Post by ubun2geek on 2011-10-06
If you have another connection available (ethernet cable) check the additional drivers.

---

### Post by Tjkent on 2011-10-10
I appreciate you guys fast response and apologize for my delayed response.

```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:15:c9:dd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.025.00-NAPI duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:40 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f020ffff

```

---

### Post by Tjkent on 2011-10-10
On top of this I have just realized that my microphone does not work as well.

---

### Post by wildmanne39 on 2011-10-10
Hi, welcome to the forum! Here is a link to get your card to work follow the directions and you should not have any problems.
[http://ubuntuforums.org/showthread.php?t=1855675](http://ubuntuforums.org/showthread.php?t=1855675)
Post 5 has a link click on it then run the commands one at a time that come up by copying and pasting, it is that simple.
Thank you

---

### Post by Tjkent on 2011-10-11
Thanks a ton.

---

### Post by wildmanne39 on 2011-10-11
Hi, let us know if you need more help.
Thank you

---

### Post by Tjkent on 2011-10-18
I am not really sure what this is but I found it in dmesg and it looks bad


[LIST=1]
[*][ 1013.210480] MlmeHardTransmitMgmtRing:: QoS NULL and PHY = 0.  MCS = 0.
[*][ 1013.210490] MlmeHardTransmitMgmtRing:: Using Low Rate to send QOS NULL!!
[*][ 1023.240635] MlmeHardTransmitMgmtRing:: QoS NULL and PHY = 0.  MCS = 0.
[*][ 1023.240645] MlmeHardTransmitMgmtRing:: Using Low Rate to send QOS NULL!!
[/LIST]

---

### Post by wildmanne39 on 2011-10-18
Hi, so can you connect?

Did you have errors when you compiled the driver?
Thank you

---

### Post by Tjkent on 2011-10-27
yes I had a few but I can't really remember them now and I can't load anything now because when I try to I get something similar to the error message below.  I have tried loading earlier kernels but I am still getting the same problem.

[ 1556.765208] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 193

---

### Post by wildmanne39 on 2011-10-27
Hi, I am not sure why you are having trouble I just compiled it on my computer and it compiled properly.

Let's do this please:
```
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo su
make clean
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Run the code one line at a time and watch for errors, warnings are ok.  It will take some of the commands a long time to complete so give them time.
Thank you

---

### Post by Tjkent on 2011-10-27
well I can't even get to my log-in screen right now, or else I would.

---

### Post by wildmanne39 on 2011-10-27
Hi, if you need to start a new thread on the login issue.
Thank you

---

