---
title: "KDE Problem"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by abou maryam on 2008-10-20
Hello
 
 i've just installed ubuntu 8.0 the Hardy Version on my laptop , and then i've installed the KDE, it seems very nice .
 
But , Unfortunately , i have somme problems with the wirless Detection (i can't detect any wirless connection) .and the Flash Disk cannot be mounted , when i try to enter to my flash disk , i got these error : the System responsed org.freedesktop.DBus.Error.AcessDenied : A security policy in place prevents this sender from sending this message to this recipient , see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume " member "Mount" error name " (unset) " destination "org.freedesktop.Hal")
 
 plz Help me to resolve these problems , how can i mount my flash disk ?
 and how can i connet to the wirless devices ??

---

### Post by xray7224 on 2008-10-20
Hello, 

For you wireless can you give us more information about your wireless card the make and model of it and also the output of 

[PHP]lsusb[/PHP]

and also

[PHP]ifconfig[/PHP]

As for your mounting problem im not sure how to help ive never had to do a lot for mounting hopefully some one else should be able to help

---

### Post by abou maryam on 2008-10-21
wassim@wassim-laptop:~$ lsusb
Bus 005 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
wassim@wassim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:10:c5:4b  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe10:c54b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23514 (22.9 KB)  TX bytes:26755 (26.1 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82300 (80.3 KB)  TX bytes:82300 (80.3 KB)

---

### Post by le bert on 2008-10-28
I have installed Kubuntu last week next to my Vista installation and was using it without any problem. I tried (unsuccessfully) to install MikTeX  yesterday (following [these]("http://miktex.svn.sourceforge.net/viewvc/miktex/miktex/branches/2.7/README.unx") rules) and after rebooting I had exactly the same errors:

- no wireless networking
- when mounting to any other disk (incl the windows partition) it gives the same org.freedesktop.hal error

Am curious if there is a common solution to these problems. 

Thanks

---

### Post by Xiong Chiamiov on 2008-10-28
Make sure you have HAL installed, and see if [this post]("http://ubuntuforums.org/showthread.php?t=353412#7") helps you.

Could you post the output of 
```

ifconfig -a

```

---

