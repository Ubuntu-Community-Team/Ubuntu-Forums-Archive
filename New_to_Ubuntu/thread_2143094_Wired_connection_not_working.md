---
title: "Wired connection not working"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by dosoe on 2013-05-07
Hello, 
I just installed ubuntu 12.4 on my pc. I can't connect him to internet. I'm using a router (speedport W920V) connected to the pc with an ethernet cable. When i go to "edit connections" i find a wired connection who worked one day ago (i installed ubuntu yesterday). When i type "sudo lshw -class network" in a terminal, he finds two networks, eth0 and eth1, but when i type "sudo ifup eth0" he says "Ignoring unknown interface eth0=eth0", the same with eth1 (even when the ethernet cable is connected). Every attempt to search speedport.ip or 192.168.2.1 have failed. When i click on the place where i can choose the connections (between the sound level and the envelope) he finds two connections: 
Wired Networks (Realtek RTL-8029(AS)) 
device not ready
Wired Networks(VIA Techologies VT6102[Rhine-II])
disconnected

The wifi is working so the router have an access to internet, but the pc can't pick wifi. 
Is there someone who could help me?
Dorian

---

### Post by Lightning Dragon on 2013-05-07
Hi,

Can you see if this works for you?

[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
[http://askubuntu.com/questions/252774/cant-connect-to-wired-internet](http://askubuntu.com/questions/252774/cant-connect-to-wired-internet)

Also check out these threads;

[http://ubuntuforums.org/showthread.php?t=1514496](http://ubuntuforums.org/showthread.php?t=1514496) (this one mentions the eth0 thing you are experiencing)
[http://ubuntuforums.org/showthread.php?t=1506854](http://ubuntuforums.org/showthread.php?t=1506854)
[http://ubuntuforums.org/showthread.php?t=1982887&page=2](http://ubuntuforums.org/showthread.php?t=1982887&page=2)

---

### Post by TheJackal12 on 2013-05-07
Can you post the results of:
```
iwconfig
```

---

### Post by dosoe on 2013-05-09
Hello, 
@TheJackal12: 
soergel@soergel-K7VT4APro:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

@LightningDragon: 
In my case, the pc don't even try to connect: 
He finds two connections but one is 
"disconnected"
and the other shows 
"device not ready", 
both in grey so i can't change anything on it.

---

### Post by dosoe on 2013-05-09
Latest news: He's now downloading updates without an internet connection(!)

---

### Post by dosoe on 2013-05-09
It seems the updates didn't help. He still can't connect to internet.

---

### Post by dosoe on 2013-05-09
Hi, 
I looked on [http://ubuntuforums.org/showthread.php?t=1284781](http://ubuntuforums.org/showthread.php?t=1284781) because i have the same realtek and typed the proposed commands (unfortunately the thread is closed)

lspci 
lsmod | grep ne2k 
ifconfig

and 
lshw

It gives 
root@soergel-K7VT4APro:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
root@soergel-K7VT4APro:~# lsmod | grep ne2k
ne2k_pci               13390  0 
8390                   18401  1 ne2k_pci
root@soergel-K7VT4APro:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d2:15:0f:8f  
          inet6 addr: fe80::2a0:d2ff:fe15:f8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19222 (19.2 KB)  TX bytes:4823 (4.8 KB)
          Interrupt:18 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:13:8f:0c:ec:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106576 (106.5 KB)  TX bytes:106576 (106.5 KB)


and for lshw (only the parts that seem connected to the network)

 *-network:0
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 00
             serial: 00:a0:d2:15:0f:8f
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
             resources: irq:18 ioport:d400(size=32)

        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: 78
             serial: 00:13:8f:0c:ec:58
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:bc00(size=256) memory:dfffbd00-dfffbdff


I hope it will help.

---

