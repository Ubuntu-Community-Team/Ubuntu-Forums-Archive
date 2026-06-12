---
title: "I need to make a network bridge"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by jmill6 on 2008-05-01
So heres the deal I need to make a network bridge,bridging my wireless card and my router. This is so i can use it to play xbox live. Any help would be appreciated. 
Thanks
Jmill
PS i have a laptop..with built in intel card.

---

### Post by ACJarrett on 2008-05-01
I hope this Thread helps you.

[http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360+gateway](http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360+gateway)

I've had to do this a couple of times.  Firestarter makes the setup easier

---

### Post by jmill6 on 2008-05-01
tht did not work,....:(:confused:

---

### Post by ACJarrett on 2008-05-01
How far does your Xbox 360 go through the Live Test before it fails?

Post your current IP and DNS setttings on your XBox 360 Please

---

### Post by jimv on 2008-05-01
1.  Buy wireless router at Wal-Mart for $30
2.  Plug wireless router into power plug on wall
3.  Plug modem into WAN port on router via ethernet cable
4.  Connect to wireless network provided by new router (should be called Linksys/Netgear/Whatever brand the router is) from computer
5.  Type 192.168.1.1 or 192.168.0.1 into Firefox.  This will bring up the config screen for the router.
6.  Configure network name/security settings as desired.
7.  Connect Xbox to wireless network provided by the router

8.  Happiness ensues.  Xbox still works if computer is turned off.

---

### Post by jmill6 on 2008-05-01
it fails at ip.
IP Address: 192.168.2.2
Subnet mask: 255.255.255.0
Gateway: 192.168.2.1
this is what i entered.
My gateway(to set my router settings)
is 192.168.1.1
so i tired that and it still did not work
is there a way i can actually bridge?

---

### Post by jmill6 on 2008-05-01
> **jimv said:**
> 1.  Buy wireless router at Wal-Mart for $30
2.  Plug wireless router into power plug on wall
3.  Plug modem into WAN port on router via ethernet cable
4.  Connect to wireless network provided by new router (should be called Linksys/Netgear/Whatever brand the router is) from computer
5.  Type 192.168.1.1 or 192.168.0.1 into Firefox.  This will bring up the config screen for the router.
6.  Configure network name/security settings as desired.
7.  Connect Xbox to wireless network provided by the router

8.  Happiness ensues.  Xbox still works if computer is turned off.

i alreayd have a router its configured. It wont let me make a wireless network bridge like I do when i dual boot vista...

---

### Post by ACJarrett on 2008-05-01
Yes, you can use your wireless card to connect your xbox to your wireless router.

Ok, So you have:

XBox 360 Settings
IP Address: 192.168.2.2
Subnet mask: 255.255.255.0
Gateway: 192.168.2.1

I assume you took your Ethernet off Roaming.  This is the "Wired" and is probably listed as eth0

These settings should be
IP Address: 192.168.2.1
Subnet mask: 255.255.255.0
Gateway: 192.168.1.1 (Or w/e your routers IP is)

If this is all setup correctly it should get to DNS when you test your xbox.

---

### Post by jmill6 on 2008-05-01
its all setup like this....still doesnt work

---

### Post by ACJarrett on 2008-05-01
Post what you get when you type ifconfig into Terminal

---

### Post by jmill6 on 2008-05-01
```
justin@justin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:4c:f0:11  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe4c:f011/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107985 (105.4 KB)  TX bytes:24114 (23.5 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113925 (111.2 KB)  TX bytes:113925 (111.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:7f:06:db  
          inet addr:192.168.1.37  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe7f:6db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:410129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464434924 (442.9 MB)  TX bytes:28424032 (27.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-7F-06-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by jmill6 on 2008-05-01
aim:
whitehallstud54

---

### Post by ACJarrett on 2008-05-01
Try changing your gateway to 192.168.1.37 on eth0 under network and see if that gets you past the IP test.

---

### Post by Steve1961 on 2008-05-01
sorry to jump in here, but why not just buy yourself a linksys wrt54gl and flash it with the dd-wrt firmware.  Then follow the instructions on the dd-wrt wiki for setting it up as a wireless bridge.  It works great with an xbox, and without all this hassle.

---

### Post by jmill6 on 2008-05-01
d

---

