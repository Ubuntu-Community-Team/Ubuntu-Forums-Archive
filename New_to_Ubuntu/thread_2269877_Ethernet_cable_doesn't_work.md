---
title: "Ethernet cable doesn't work"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by limadepaula1 on 2015-03-18
hi guys
my wireless internet does work normally, but when i try use cable it doesnt work, i have looked similar problams but it wasnst helpfull

here some outputs

lshw -C network
```

andre@limadepaula:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:4d:c3:4f:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-31-generic firmware=N/A ip=192.168.0.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
andre@limadepaula:~$ 

```

ifconfig
```

andre@limadepaula:~$ ifconfig
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.27.224.1  P-t-P:172.27.224.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:77098 (77.0 KB)

as0t1     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.27.228.1  P-t-P:172.27.228.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:77098 (77.0 KB)

as0t2     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.27.232.1  P-t-P:172.27.232.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:77098 (77.0 KB)

as0t3     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.27.236.1  P-t-P:172.27.236.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 B)  TX bytes:77098 (77.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6092457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6092457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:[16808681428]("tel:16808681428") (16.8 GB)  TX bytes:[16808681428]("tel:16808681428") (16.8 GB)

wlan0     Link encap:Ethernet  HWaddr 00:26:4d:c3:4f:87  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:4dff:fec3:4f87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6644015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4399477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:[3682857125]("tel:3682857125") (3.6 GB)  TX bytes:563045375 (563.0 MB)

andre@limadepaula:~$ 

```



i gonna be really thankful if u can help me

---

### Post by Vladlenin5000 on 2015-03-18
Hello and welcome.

I can't see any Ethernet adapter in the hardware you posted. What machine are we talking about?

---

### Post by limadepaula1 on 2015-03-18
> **Vladlenin5000 said:**
> Hello and welcome.

I can't see any Ethernet adapter in the hardware you posted. What machine are we talking about?

I have got a toshiba nb305

this is the output of ispci

```

andre@limadepaula:~$ sudo lspci
[sudo] password for andre: 
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
andre@limadepaula:~$ 


```

---

### Post by deadflowr on 2015-03-19
Please use code tags when posting the output from the terminal.
It reads better than using quote tags.

Also, per the thread, I see no Ethernet listed in the lspci output.
Is the Ethernet perhaps disabled in the BIOS/UEFI?

---

### Post by Vladlenin5000 on 2015-03-19
Indeed. The Ethernet is still a no show... Only the wireless appears.
As suggested it may have been disabled in BIOS (this Toshiba is pre-UEFI) but it can be faulty as well.

---

### Post by limadepaula1 on 2015-03-19
Yes it was the bios I wnet there and looked for it, thanks

---

