---
title: "ubuntu installed, wired connection not working"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Nihilithik on 2012-02-16
Hello again UbunuGurus, installed ubuntu 11.10 into my pc. I cant get the wired connection to start. I've gone through forums and googled around abit, as i am want to do. Seems there is no easy fix though. Can a brother get a hand?

---

### Post by Nihilithik on 2012-02-16
ran ipconfig eth0

[sudo] password for nihilithik: 
eth0      Link encap:Ethernet  HWaddr 00:22:15:67:58:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:42

---

### Post by Nihilithik on 2012-02-16
Hey Happy Helpers,

I installed 11.10 on my pc, but i can't figure out why my wired connection wont turn on. i ran ipconfig eth0 and got this: 
[sudo] password for nihilithik: 
eth0 Link encap:Ethernet HWaddr 00:22:15:67:58:bd 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:42

this means it can see my ethernet card but won't turn it on? 

i've been searching the forum and googling, but to no avail.

any help or even a nudge in the right direction would be very appreciated.
thanks.

---

### Post by Iowan on 2012-02-16
> **Nihilithik said:**
> ran ipconfig eth0
Hopefully it was **ifconfig**... ;)

Please post results of: **sudo lshw -C network**
That should (hopefully) provide more information about the interface/card.
The MAC address suggests it's made by ASUSTek COMPUTER INC.

---

### Post by Nihilithik on 2012-02-17
Thanks Iowan, i'm sure this is an old hat issue, and please believe that i did do my very best to find this fix in both forums. (and the ipconfig def a typo)


[sudo] password for nihilithik: 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:22:15:67:58:bd 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:42 ioport:e800(size=256) memory:fbfff000-fbffffff memory:faff0000-faffffff memory:fbfc0000-fbfdffff

---

### Post by Nihilithik on 2012-02-17
ran lshw -c network 


[sudo] password for nihilithik: 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:22:15:67:58:bd 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:42 ioport:e800(size=256) memory:fbfff000-fbffffff memory:faff0000-faffffff memory:fbfc0000-fbfdffff 

if this helps anyone to help me...cheers!

---

### Post by Nihilithik on 2012-02-18
After a few days now of searching and lurking IRC, i still have no solution. I was wondering if maybe installing an earlier version of ubuntu might fix this. Does any one out there have any idea what version of ubuntu i would need to install that would be compatible with a  RTL8111/8168B PCI Express Gigabit Ethernet controller?

---

### Post by Nihilithik on 2012-02-18
Does any one out there have any idea what version of ubuntu i would need to install that would be compatible with a RTL8111/8168B PCI Express Gigabit Ethernet controller? Even if i have to go back a few versions.

---

### Post by uRock on 2012-02-18
Duplicate threads have been merged. Please do not create multiple threads on the same topic.

---

### Post by Nihilithik on 2012-02-20
Sorry about the multi-thread. I should have done more than skim forum rules. Won't happen again. Still haven't been able to solve this. A little help here? :sad:

---

