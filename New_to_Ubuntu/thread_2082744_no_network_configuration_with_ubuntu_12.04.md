---
title: "no network configuration with ubuntu 12.04"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by mokashung on 2012-11-10
hi!
I upgraded my ubuntu yesterday to 12.04, and suddenly i have no internet connection. before i did have, now it says that the network configuration is not compatible with this version of ubuntu (or so, i don't remember it exactly), then it waits 60 seconds and then boots without network configuration.

I've seen people with similar problems on this forum, but the answers 
a° didn't work for me
b° were ununderstandable for me...

and, i don't see any internet icon on the top right corner anymore, neither do i find Network Manager...

this is the outcome of some commands:

madelief@madelief-desktop:~$ sudo lshw -C network  
 [sudo] password for madelief:  
   *-network:0 DISABLED     
        description: Wireless interface  
        product: RT2561/RT61 802.11g PCI 
        vendor: Ralink corp.  
        physical id: 6  
        bus info: pci@0000:00:06.0  
        logical name: wlan0  
        version: 00  
        serial: 00:10:60:67:39:f6  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rt61pci driverversion=3.2.0-32-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg  
        resources: irq:0 memory:ffff8000-ffffffff  
 

 *-network:1 DISABLED  
        description: Ethernet interface  
        product: VT6102 [Rhine-II]  
        vendor: VIA Technologies, Inc.  
        physical id: 12  
        bus info: pci@0000:00:12.0  
        logical name: eth0  
        version: 74  
        serial: 00:40:d0:96:23:a6  
        size: 100Mbit/s  
        capacity: 100Mbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full latency=128 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s  
        resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff  
 

 madelief@madelief-desktop:~$ sudo iwconfig  
 [sudo] password for madelief:  
 lo        no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
            
 eth0      no wireless extensions.  
 

 madelief@madelief-desktop:~$ sudo ifconfig  
 [sudo] password for madelief:  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:2160 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:2160 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:130600 (130.6 KB)  TX bytes:130600 (130.6 KB)  
 

 any help possible?

---

### Post by robbie 348 on 2012-11-10
I had a similar problem. All I did was switch off the computer, unplug it for a minute or so, plug it back in and re-boot and the network was there again.

---

### Post by mokashung on 2012-11-10
jep, i tried that too but it didn't work...

---

### Post by mokashung on 2012-11-10
I tried a bit further and I have a new answer in my terminal:

madelief@madelief-desktop:~$ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback  
 

 

 auto dsl-provider  
 iface dsl-provider inet ppp  
 pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf  
 provider dsl-provider  
 

 auto eth0  
 iface eth0 inet manual  
 
Of course I have no idea of what all this means, it's just something I tried, based upon what i read in another thread...

I also have to say, that at my place i have a router, but here (in another house, where we have a second computer which allows me to go on the internet) I'm not sure whether I'm connected to a router or a modem...

can anyone deduce that from what is written above? and is it important for the solution of the problem?

---

### Post by mokashung on 2012-11-10
In the mean time I also tried what was written on this page:

[http://www.necopost.com/2012/06/network-manager-not-running-error-on.html](http://www.necopost.com/2012/06/network-manager-not-running-error-on.html)

it worked only in the sense that now I don't have the messages of "waiting sixty more minutes etc." in the beginning, and that now I already see an internet icon at the top right corner of my screen.

but I still can't connect...

it says "wired network disconnected" (and it doesn't manage to connect when I try to), and about my wireless it says: "wireless networks device not ready".

---

### Post by mokashung on 2012-11-10
i rebooted the computer another time, and now it works..
so the solution is explained on the link which I posted above, and it works! :)

---

