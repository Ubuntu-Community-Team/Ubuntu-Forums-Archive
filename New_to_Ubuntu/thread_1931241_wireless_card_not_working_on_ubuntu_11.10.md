---
title: "wireless card not working on ubuntu 11.10"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by kalimojo on 2012-02-25
lspci shows

02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: rt5390sta

iwconfig doesnt show up the ra0.

any help appreciated.

---

### Post by sanderj on 2012-02-25
> **kalimojo said:**
> lspci shows

02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: rt5390sta

iwconfig doesnt show up the ra0.

any help appreciated.

[http://lmgtfy.com/?q=RT5390+Wireless+ubuntu](http://lmgtfy.com/?q=RT5390+Wireless+ubuntu)

---

### Post by kalimojo on 2012-02-25
> I had the same problem when I upgraded my HP DM1Z laptop from 11.04 to 11.10, but it was easy to fix.

Under 11.04 I got my Wi-Fi working using [these instructions]("http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010")   on 6by9.net. For 11.10 I had to comment out "rt5390sta" in  /etc/modules  and "blacklist rt2800pci" in  /etc/modprobe.d/blacklist.conf. After a  reboot my Wi-Fi came right up.

Hope this helps. hopefully that will work

---

### Post by kalimojo on 2012-02-25
>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




iwconfig can see it but it wont connect to my AP.

---

### Post by kalimojo on 2012-02-25
after a reboot i get 

ra0       Link encap:Ethernet  HWaddr 90:00:4e:2b:96:06  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe2b:9606/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1473941 (1.4 MB)  TX bytes:8612 (8.6 KB)
          Interrupt:16

---

