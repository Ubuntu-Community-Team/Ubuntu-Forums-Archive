---
title: "no wireless extensions."
date: 2017-07-28
forum: New to Ubuntu
---

### Post by unname on 2017-07-28
hello,
 
im a new with linux. i need some help to solve my problem. my terminal cant detect my wireless extension.


unname@ubuntu:~$ iwconfig
ens33     no wireless extensions.


lo        no wireless extensions.


unname@ubuntu:~$ ifconfig
ens33     Link encap:Ethernet  HWaddr 00:0c:29:22:b4:a0  
          inet addr:192.168.96.139  Bcast:192.168.96.255  Mask:255.255.255.0
          inet6 addr: fe80::eaf7:1259:41c3:2d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1957 (1.9 KB)  TX bytes:7983 (7.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15273 (15.2 KB)  TX bytes:15273 (15.2 KB)

---

### Post by grahammechanical on 2017-07-28
ens33 is most likely your ethernet adapter. It will not have a wireless extension. We have to ask: Does your machine have a wireless/WiFi adapter? Is it switched on in the machine's BIOS/UEFI setup utility? Do you have Microsoft Windows installed? If you do, then is WiFi switched off in Windows? If it is then it is unlikely that it will be switched on in Ubuntu.

What version of Ubuntu are you using. Each new version of Ubuntu has changes or improvements. For example, I am using the 17.10 development version and iwconfig is not longer installed. I have to use nmcli commands to get information about my network devices. So, it is useful to us in helping you that you tell us the version of Ubuntu so that we do not give instructions that do not make sense with your version.

Regards.

P.S. Try these commands
```
rfkill list
```

If the response is #soft blocked# then the Wifi adapter is switched off by software and that may mean that a driver will need to be installed.

If the response if #hard blocked# then that will mean that there is a hardware switch that has set the Wifi Adapter to off. Laptops may have a key combination to switche on the WiFi.

This command may work

```
rfkill ublock wifi
```

---

### Post by lidiaceae on 2017-11-19
> **grahammechanical said:**
> ens33 is most likely your ethernet adapter. It will not have a wireless extension. We have to ask: Does your machine have a wireless/WiFi adapter? Is it switched on in the machine's BIOS/UEFI setup utility? Do you have Microsoft Windows installed? If you do, then is WiFi switched off in Windows? If it is then it is unlikely that it will be switched on in Ubuntu.

What version of Ubuntu are you using. Each new version of Ubuntu has changes or improvements. For example, I am using the 17.10 development version and iwconfig is not longer installed. I have to use nmcli commands to get information about my network devices. So, it is useful to us in helping you that you tell us the version of Ubuntu so that we do not give instructions that do not make sense with your version.

Regards.

P.S. Try these commands
```
rfkill list
```

If the response is #soft blocked# then the Wifi adapter is switched off by software and that may mean that a driver will need to be installed.

If the response if #hard blocked# then that will mean that there is a hardware switch that has set the Wifi Adapter to off. Laptops may have a key combination to switche on the WiFi.

This command may work

```
rfkill ublock wifi
```



Hi, I have the same problem.
Mi ubuntu version is 16.04 and I have windows 10 too. I really need your help. In this version iwconfig is installed, but I dont know what can I do?

---

