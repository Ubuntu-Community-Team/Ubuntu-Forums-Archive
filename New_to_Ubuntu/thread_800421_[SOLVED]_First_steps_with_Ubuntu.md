---
title: "[SOLVED] First steps with Ubuntu"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nabab on 2008-05-19
Hi there,

I have just tried Ubuntu from a boot CD, everything worked fine except that I got a message related to my wireless card:

> 
Proprietary drivers are being used to make this computer work properly.

Device driver:
- Atheros Hardware Access Layer (HAL) (in use)
- Support for Atheros 802.11 wireless LAN cards (in use)


I couldn't find the wireless card in the Network menu, so I guess it was not recognized at the end.

I have been on the Atheros website, and they have released a Linux driver. Do you know if I can load a driver when I'm using the OS from the boot CD?

The only thing because of which I wouldn't install Ubuntu would be if my WiFi card was not recognized. How big do you reckon the risks are?

Many thanks,

Thomas

---

### Post by jakupl on 2008-05-19
####### really stupid post... sorry... had to delete my stupidity. #########

---

### Post by nabab on 2008-05-20
Hi, 

Nobody can tell me?

Thanks,

Thomas

---

### Post by hyper_ch on 2008-05-20
open a terminal and output the result of this:

```

lspci | grep Ath

```

```

lsusb | grep Ath

```

```

ifconfig

```

```

iwconfig

```

---

### Post by hyper_ch on 2008-05-20
and next time use a topic title that reflects the content of the post... a generic "noob here" or "help needed" is not really appreciated ;)

You know, when you want people try and help you, you should also help the people that try to help you ;)

---

### Post by nabab on 2008-05-20
Sorry about that, I've just edited the title.

I will give a try to this tonight and will post the result.

Many thanks,

Thomas

---

### Post by nabab on 2008-05-20
I typed the command requested by hyper_ch and here is the result:
```
ubuntu@ubuntu:~$ lspci | grep Ath
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
ubuntu@ubuntu:~$ lsusb | grep Ath
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:1f:bd:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:475500 (464.3 KB)  TX bytes:475500 (464.3 KB)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Any idea if it will be a concern having this WiFi card working, knowing the Linux drivers exist? Is it possible to install drivers when you're only using the boot CD to test? (I'd say you can't but hopefully you'll say the opposite...)

Thanks!

Thomas

---

### Post by hyper_ch on 2008-05-20
now you know your model and it's not auto-recognized by ubuntu... so you have to search this forum how to get it up and running.

I guess you'll have to use ndiswrapper and runn it through your windows drivers.

---

