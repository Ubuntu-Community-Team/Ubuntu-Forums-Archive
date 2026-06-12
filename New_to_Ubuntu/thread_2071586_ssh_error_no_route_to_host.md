---
title: "ssh error no route to host"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by weatherscomputers on 2012-10-15
hello everyone
I have two PCs connected to a wireless router. One of them is connected wirelessly and one ethernet, they both were assigned ips of 192.168.1.3 and 192.168.1.4 respectively. They both are able to connect to the internet and both have ssh installed.

problem im getting is when I ssh kyle@192.168.1.4 it comes back with error "no route to host" . Im able to ssh into mark@192.168.1.3 from my android tablet but i cant ssh to 192.168.1.4 either. 

I checked the firewall status using ufw status and it said it was inactive, this goes for both PCs so i dont think its a firewall problem 

Does anyone have any ideas?

Also PC 192.168.1.3 is running ubuntu 12.04 and PC 192.168.1.4 is running xubuntu 12.04

Thanks ahead of time!

---

### Post by Pieman15 on 2012-10-15
Can you ping 192.168.1.4? I'd restart the router just in case.

---

### Post by weatherscomputers on 2012-10-15
I tried that too I get "destination host unreachable"

---

### Post by CharlesA on 2012-10-15
Run this from that box with an ip of 192.168.1.4:

```
ifconfig
```

---

### Post by weatherscomputers on 2012-10-15
typing ifconfig on box gives me following: I now notice the ip has changed back to a DHCP address....i dont know what gives I had it set earlier and did an ifconfig and it showed 192.168.1.4 I did it in the network manager on xubuntu

```
eth0      Link encap:Ethernet  HWaddr 00:40:ca:ae:23:0e  
          inet addr:192.168.1.175  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4438:58e2:1234:240:caff:feae:230e/64 Scope:Global
          inet6 addr: fe80::240:caff:feae:230e/64 Scope:Link
          inet6 addr: 2002:4438:58e2:1234:39e4:2032:9498:9e21/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5401753 (5.4 MB)  TX bytes:615960 (615.9 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:662 (662.0 B)  TX bytes:662 (662.0 B)

```

---

### Post by CharlesA on 2012-10-15
Did you set it as a static IP in the GUI? Check the settings in Network Manager and see what it says.

But yeah, the reason it wouldn't work is due to the IP change. ;)

---

### Post by weatherscomputers on 2012-10-15
Yeah i set the static in the gui before i did all this, but now the network manager wired connection is greyed out and says "not managed"

---

### Post by CharlesA on 2012-10-16
Check this out:
[http://askubuntu.com/questions/71159/network-manager-says-device-not-managed](http://askubuntu.com/questions/71159/network-manager-says-device-not-managed)

---

### Post by weatherscomputers on 2012-10-16
Thanks! it worked....i was able to set it statically with the /network/interface file 
I successfully logged in this morning. thanks again!

---

