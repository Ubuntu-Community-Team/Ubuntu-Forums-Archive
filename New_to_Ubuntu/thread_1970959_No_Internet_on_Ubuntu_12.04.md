---
title: "No Internet on Ubuntu 12.04"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Delta 397 on 2012-05-01
Hi all,

I have just successfully installed Ubuntu 12.04 on my MBP however the ethernet connection doesnt work as well as the wifi.  It sys that Im missing some firmware.  I know you might need more info but im still new with Linux.  Any advice would be appreciated.

---

### Post by sir_cheats_a_lot on 2012-05-02
sounds like you might have the pesky broadcom chipsets.   please open the terminal, and type "lspci" without the quotes, and copy and paste the output results here so that we may help.

---

### Post by Delta 397 on 2012-05-02
Here is the code...

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)

---

### Post by chamber on 2012-05-02
Type

```
ifconfig
Ip addr
```

And post the results. Remember to use a code box for your results.

---

### Post by Delta 397 on 2012-05-02
Ok here is the code for the ifconfig and ip addr as well.

```
mitch@mitch-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:07:54:56:e8:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3344 (3.3 KB)  TX bytes:3344 (3.3 KB)

mitch@mitch-Ubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 3c:07:54:56:e8:11 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether b8:8d:12:2e:9f:80 brd ff:ff:ff:ff:ff:ff
mitch@mitch-Ubuntu:~$
```

---

