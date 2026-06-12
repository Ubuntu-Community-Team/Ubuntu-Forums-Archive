---
title: "Internet Problem"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-28
I currently have 2 platforms

[platform1(UBUNTU)] [platform2(WINDOWS)]

I removed the harddrive on platform1 where my ubuntu is installed and moved it to platform2 and moved my windows harddrive to platform1, but the internet on my Ubuntu no longer works. :confused:

---

### Post by Fire_Chief on 2008-07-28
Is the network card in both platforms the same? If not, you need to reconfigure your network connection on the Ubuntu system to use the new network card detected (assuming it is detected).

Cheers!

---

### Post by waterrr on 2008-07-28
How would I reconfigure it, and I'm assuming it's different because there is no internet when I switch the harddrives

---

### Post by halitech on 2008-07-28
open a terminal
```
ifconfig
```
post the output here

---

### Post by waterrr on 2008-07-28
in ifconfig, i got this as a return
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23572 (23.0 KiB)  TX bytes:23572 (23.0 KiB)
```

---

### Post by halitech on 2008-07-28
ok, so its not seeing the network card at all. was the card working in windows?

---

### Post by waterrr on 2008-07-28
when the windows was originally there, the internet was working fine

---

### Post by Het Irv on 2008-07-28
Is this Internet connection Wired or Wireless?
If Wired is it a PCI card or built in
If Wireless is it a card or USB?

---

### Post by waterrr on 2008-07-28
it's a wired connection, not sure if its a pci or built in

---

### Post by halitech on 2008-07-28
open a terminal and post the output of
```
lspci
```

---

### Post by waterrr on 2008-07-28
output of lspci
```
0000:00:00.0 Host bridge: Intel Corporation E7520 Memory Controller Hub (rev 09)0000:00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 09)
0000:00:04.0 PCI bridge: Intel Corporation E7525/E7520 PCI Express Port B (rev 09)
0000:00:05.0 PCI bridge: Intel Corporation E7520 PCI Express Port B1 (rev 09)
0000:00:06.0 PCI bridge: Intel Corporation E7520 PCI Express Port C (rev 09)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:01:00.0 PCI bridge: Intel Corporation 80332 [Dobson] I/O processor (A-Segment Bridge) (rev 06)
0000:01:00.2 PCI bridge: Intel Corporation 80332 [Dobson] I/O processor (B-Segment Bridge) (rev 06)
0000:02:05.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)
0000:05:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
0000:05:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
0000:06:07.0 Ethernet controller: Intel Corporation 82541GI/PI Gigabit Ethernet Controller (rev 05)
0000:07:08.0 Ethernet controller: Intel Corporation 82541GI/PI Gigabit Ethernet Controller (rev 05)
0000:09:0d.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

---

### Post by halitech on 2008-07-28
it seems to be showing 2 network cards

[color=red]0000:06:07.0 Ethernet controller: Intel Corporation 82541GI/PI Gigabit Ethernet Controller (rev 05)
0000:07:08.0 Ethernet controller: Intel Corporation 82541GI/PI Gigabit Ethernet Controller (rev 05)
[/color]

do you have 2 networ cards installed?

---

### Post by waterrr on 2008-07-28
Yes i do

---

### Post by waterrr on 2008-07-28
Anybody have a solution?

---

### Post by Het Irv on 2008-07-28
And you have tried both of the cards? 

Normally Ubuntu will recognize your LAN ports automagically, but the Hard drive switch might have messed something up.

---

### Post by waterrr on 2008-07-28
yes i've tried both cards but both do not work - is there anything i can do to make the ubuntu recognize recognize it?

---

### Post by Fire_Chief on 2008-07-28
What happens if you try```
sudo ifconfig eth0 dynamic
sudo ifup eth0
```

---

### Post by waterrr on 2008-07-28
it says there is no such device

---

### Post by Fire_Chief on 2008-07-28
You could try to probe for it and see if the system will assign the driver.```
sudo modprobe e1000
``` I think this is the right driver for the NIC.

---

### Post by waterrr on 2008-07-28
that command line brings up nothing for me

---

### Post by xnostradamusx on 2008-07-28
got the same problem in my brothers desktop its pci network card,

it seems it is not recognized by ubuntu

---

### Post by Fire_Chief on 2008-07-28
That's ok, it's not supposed to really output anything unless it has an error. But since it did not give an error, do you now have the e1000 module loaded?```
sudo lsmod | grep e1000
```
If so, what do you now see from ifconfig?
Hopefully you now have an eth0 interface that is usable.

Cheers!

---

### Post by waterrr on 2008-07-28
Still didnt work :(

i get this in ifconfig

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23572 (23.0 KiB)  TX bytes:23572 (23.0 KiB)
```

---

### Post by Fire_Chief on 2008-07-29
But did it show the module loaded?

---

### Post by JoneYee on 2008-07-29
Are the nics configured to be teamed at the switch/router?  ( I doubt it, but It's worth asking.

What happens if you bypass the rotuer and cable directly to your cable/dsl modem?

Have you tried deactivating one of the nics?

Are the NICS DHCP or static?

---

