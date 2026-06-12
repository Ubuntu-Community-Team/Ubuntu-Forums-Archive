---
title: "Wireless Lost, with formatting of windows/Ubuntu installation"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Henrywantstobeapenguin on 2008-05-16
Hello,

When running off the live CD, my friend could access my his wireless. He decided to install Ubuntu from a MD5checksum/CD Integrity checked 8.04 Live CD.

We formatted his hard drive, then partitioned it and installed Ubuntu, as well as reinstalling windows.

His wireless no longer works. :(

We ran the hardware check and it correctly identified his wireless card as:-

Intel Corporation PRO/Wireless 2200BG Network 

But its not working, or detecting any networks.

Please Help! 

Many thanks 

Henry

---

### Post by pro003 on 2008-05-16
type in terminal:

```
ifconfig ath0 up
```

```
ifconfig wifi0 up
```

```
ifconfig wlan0 up
```

```
ifconfig
```

show the output of the "ifconfig" in your next post after...

---

### Post by Henrywantstobeapenguin on 2008-05-16
Thanks very much for your help: - Here is the entire terminal output/trasnscript.

jack@jack-laptop:~$ ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
jack@jack-laptop:~$ ifconfig wifi0 up
wifi0: ERROR while getting interface flags: No such device
jack@jack-laptop:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
jack@jack-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:6f:3f:95  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2202 (2.1 KB)  TX bytes:9282 (9.0 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:f0:0a:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78700 (76.8 KB)  TX bytes:78700 (76.8 KB)

Thanks very much

Henry

---

### Post by pro003 on 2008-05-16
is your machine connected with other machine(s)?

you have active eth0 as you can see... now do you use user name and password to log in on your ISP?

---

