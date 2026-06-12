---
title: "Ocelot issue with E220 3G dongle"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-10-23
Hi,    I've just upgraded from Natty to Ocelot and until December I'm dependent on a Huawei E220 3G dongle for my internet access.

The dongle was connecting fine in Natty,  but I'm having a lot of difficulty getting it to connect on Ocelot.    When I try to connect, instead of connecting, it tells me "You are now registered on the home network" and then it eventually times out with a Not Connected message.  I've checked that the 3G account settings in Ocelot are the same as they were in Natty (basically a default setting without need of any APN or a dialup code).  Repeated attempts only time out with a Not connected message.

The only way I've been able to get on-line with Ocelot is to close everything and go over to my Windows XP partition and go briefly on-line there using Huawei's own Mobile Connect software.   At first Windows indicates that it's recognised the USB presence of the dongle with a "plong-pling" sound,  then a brief "pling-plong" as it disconnects,  followed quickly by a 2nd "plong-pling" as the Huawei software re-recognises it as a modem instead of as a flash drive.   Only after this triple Windows pling-plonging sequence can the system connect on-line.  

How does all this help me to connect on Ocelot?   Well if I then shut down Windows and restart Ocelot,  I can usually get the dongle to connect on Ocelot.  And if I disconnect for a period while Ocelot is still up and running,  I can usually reconnect again without difficulty,  but if I close Ocelot,  then when I reopen it again,   I'm back to square one with the original "You are now registered on the home network" message instead of connecting,  and I have to go back to Windows to re-initialise the dongle.

This problem has only started since I upgraded from Natty to Ocelot.  I don't really understand the initialisation process that Windows Huawei software performs on the dongle when it's first plugged in,  but somehow it manages to change it from looking like a flash drive into looking like a modem on the 2nd "plong-pling" there.    Whatever it does,  Natty used to be able to handle it and now Ocelot doesn't.  

Of course it's not much fun having to close everything in Ocelot and go over to Windows to re-initialise my dongle every time I want to log-in.    Any bright ideas,  anyone?

---

### Post by Sleepy-zz-John on 2011-10-25
Bump

---

### Post by Sleepy-zz-John on 2011-10-26
Bump again

---

### Post by amjjawad on 2011-10-26
What system are you using? Lubuntu?

```
sudo lshw -C network
```

---

### Post by Sleepy-zz-John on 2011-10-27
Thanks amjjawad
No,  I'm on basic Ubuntu 11.10 with an Acer Aspire One netbook, AMD C-50Processor x 2.
from sudo lshw -C network
 ```
*-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:71:3e:8d
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: c0:f8:da:96:ae:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:90100000-9010ffff 

```
from ifconfig:
```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.223.174.234  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:4424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3392825 (3.3 MB)  TX bytes:577039 (577.0 KB)
```
from lsusb
```

Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem
```

---

### Post by Sleepy-zz-John on 2011-10-27
Let me add this observation:   
Once I've got this E220 working and connected,  it can survive offline/online disconnections and reconnections,  Ocelot to Ocelot system restarts,  and Windows to Ocelot restarts.  The common factor on these being that it remains powered up all the time.   It does not survive depowering, so after depowering, I can only get it to work again with a visit to its Huawei Windows Mobile Connect programme.   .

---

### Post by Sleepy-zz-John on 2011-10-27
Here are the results of some system restart and USB disconnection tests I've now tried with my E220:

1.  Starting from on-line status on my installed Ocelot and restarting to a live CD Natty session,  my E220 was able to connect again OK

2.  Starting from a Natty Live CD on-line session and disconnecting my E220's USB cable for 5 minutes,  and then reconnecting the USB cable back into the same live Natty CD session,  my E220 was able to connect again OK

3.  Starting from a Natty Live CD on-line session and restarting to go back to my installed Ocelot, but with a 5 second powerdown in between,  my E220 failed to connect again, The only way I could get back on-line again was to restart and go to Windows and use Huawei's Mobile Connect app there  

4.  Starting from on-line status on my Windows with Huawei's Mobile Connect and restarting to my installed Ocelot,  my E220 was able to connect again OK

5.  Starting from an on-line status on my installed Ocelot,  disconnecting and then unplugging my E220's USB cable for 20 seconds,  followed by replugging the USB cable back into the same installed Ocelot session, my E220 failed to connect again and the only way I could get back on-line was to close and go over to Windows and Huawei's Mobile Connect app there.    

So these tests indicate that after a powerdown,  only Windows' Huawei Mobile Connect or Natty can get it going again.   Ocelot cannot.

---

### Post by Sleepy-zz-John on 2011-10-29
Bump

---

### Post by mörgæs on 2011-10-29
This is a known bug in 11.10:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/868034](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/868034)

There is some advice in the bug report. If that does not work, best you can do is to add your findings there and stick to 11.04 meanwhile.

---

### Post by gs777 on 2012-02-03
visit [here]("http://www.unlockdongle.blogspot.in/") for unlock codes. I give them nominal price

---

