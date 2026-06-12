---
title: "[SOLVED] How can I determine the IP address of my PC?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-09-27
My PC is on a Network and need to know the IP address.  I am sure there is a simple command but I can't find it.

---

### Post by Bradtek on 2008-09-27
```
ifconfig
```

I think

---

### Post by curiousnoob on 2008-09-27
I get this: 
eth0      Link encap:Ethernet  HWaddr 00:13:20:8f:6a:15  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe8f:6a15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96371314 (91.9 MB)  TX bytes:3803076 (3.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134600 (131.4 KB)  TX bytes:134600 (131.4 KB)

I know that my router is 192.168.1.1  but I am not sure what the PC itself is.

---

### Post by lisati on 2008-09-27
> **Bradtek said:**
> ```
ifconfig
```

I think

Yes - ifconfig can show you the IP address on your local network. If you ever need information on your IP address on the internet, then [http://whatismyipaddress.com/](http://whatismyipaddress.com/) can provide you with some interesting information.

---

### Post by tangibleorange on 2008-09-27
yeah this bit is the IP address:

**inet addr:192.168.1.100**

---

### Post by curiousnoob on 2008-09-27
I'm confused.  Both my PC AND my router are 192.168.1.1?  I thought they had to be different.

---

### Post by lisati on 2008-09-27
> **curiousnoob said:**
> I get this: 
eth0      Link encap:Ethernet  HWaddr 00:13:20:8f:6a:15  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe8f:6a15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96371314 (91.9 MB)  TX bytes:3803076 (3.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134600 (131.4 KB)  TX bytes:134600 (131.4 KB)

I know that my router is 192.168.1.1  but I am not sure what the PC itself is.

Your computer's IP address on your network is this one:>  inet addr:192.168.1.100

---

### Post by j.bunce on 2008-09-27
That's right. Devices on a network must have different IP Addresses.

---

### Post by issih on 2008-09-27
Your router is 192.168.1.1, your pc 192.168.1.100

each number between the dots ranges from 0 to 255. In a normal home network the first 3 numbers match for all pcs/networked device, only the last digit changes.

Note that if your router uses dhcp to assign the addresses to the pcs connected to it, your pc is not guaranteed to always have the same number assigned to it, they can change.

Finally note that this address only applies on your home network, i.e. if from your pc you enter 192.168.1.1 in your browser address bar you will get the router's admin web server, but if you did that from another pc out in the wilds of the internet, you would not get to your router...that ip address is local to you network, not global.

Hope that helps

---

### Post by curiousnoob on 2008-09-27
> **issih said:**
> Your router is 192.168.1.1, your pc 192.168.1.100

each number between the dots ranges from 0 to 255. In a normal home network the first 3 numbers match for all pcs/networked device, only the last digit changes.

Note that if your router uses dhcp to assign the addresses to the pcs connected to it, your pc is not guaranteed to always have the same number assigned to it, they can change.

Finally note that this address only applies on your home network, i.e. if from your pc you enter 192.168.1.1 in your browser address bar you will get the router's admin web server, but if you did that from another pc out in the wilds of the internet, you would not get to your router...that ip address is local to you network, not global.

Hope that helps

I'm an idiot.  For some reason I thought .1 and .100 were the same thing.  Must be a flashback to math class.  
Thanks everyone for your patience.

---

