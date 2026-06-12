---
title: "sudo modprobe ath_pci at boot"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-04-28
Got my wireless working today - hooray!  But I`m struggling to get it to work when I turn the laptop on. I have to type sudo modprobe ath_pci.
  How do I make it work straight away?
Thankyou.

---

### Post by Michael.Godawski on 2008-04-28
Can you please post the output of these terminal commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by nothingspecial on 2008-04-28
Thanks for helping.

: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:20:e0:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.69 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f0:0f:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 
mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s





and





  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:20:e0:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.69 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f0:0f:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
rob@rob-compaq-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"BTHomeHub-EF98"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:7F:27:85   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:4631  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Michael.Godawski on 2008-04-28
Try this:

Add to /etc/modules  the line ath_pci
```
gksudo gedit /etc/modules
```

after that, edit /etc/modprobe.d/options 
```
gksudo edit /etc/modprobe.d/options
```
and add the line
```
options ath_pci rfkill=0
```

---

### Post by nothingspecial on 2008-04-28
You sir are a genius. That`s cracked it. Thanks!

I`m not being rude and I`m really grateful for your help but for anyone trying to follow this thread at a later date -

gksudo edit /etc/modprobe.d/options

should be

gksudo gedit /etc/modprobe.d/options

I`m not trying to be clever and I`m really grateful for your help, it`s just that I`ve been doing this for a few weeks now and if I`d just installed that would have completely thrown me.

Once again thanks

---

### Post by Michael.Godawski on 2008-04-28
oops bad typo. :)

of course it is gedit. And good to hear you solved this.

---

### Post by gusanto on 2008-05-31
> **Michael.Godawski said:**
> Try this:

Add to /etc/modules  the line ath_pci
```
gksudo gedit /etc/modules
```

after that, edit /etc/modprobe.d/options 
```
gksudo edit /etc/modprobe.d/options
```
and add the line
```
options ath_pci rfkill=0
```

Hi there,
I have the same problem on my Sony Vaio VGN-NR120E.  I tried your suggestion and had no effect.

sudo lshw -C network
>  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1f:8b:1a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:d9:dd:a7:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.101 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


iwconfig 
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DFI2000"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:47:AC:EB   
          Bit Rate:6 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-44 dBm  Noise level=-92 dBm
          Rx invalid nwid:784  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Is there any specific solution for this problem?
Many thanks.

---

### Post by zxmon21 on 2008-06-01
I just want to say that this thread helped me figure out how to permanently fix some settings for my TV-card.

I just had to put an option in /etc/modprobe.d/options and that worked like a spell :)

Thanks to all people who post advice here!

---

### Post by codyhendrix2 on 2008-11-08
just wanted to say thanks to Michael.Godawski for the info.:D thanks!
:guitar:

---

