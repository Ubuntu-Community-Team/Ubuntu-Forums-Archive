---
title: "Internet"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by Olipton on 2013-02-08
I have trying to connect to the internet with a Belkin n750 DB adapter and router.

I have found the basic info of it, but it is not auto-connecting, nor can i see any networks.

Info: (may be slightly off, due to the fact that i am not able to copy and past through computers)

description: Ethernet interface

*blah blah blah*
Vendor: realtek semiconductor
 logical name: eth0
blah blah

now to the good stuff
configuration: autonegotiation= on broadcast=yes driver=r8169 driverversion=2.3lk-Napi duplex=haalf firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no latency=0 multicast=es port=MII speed=10mbit/s

I forget the command, but when I run some network command, it says: eth0 no *something or other*
lo no *something or other*


I realize i don't have much info, but does anyone know how to get usb adapters and such working.

---

### Post by mapes12 on 2013-02-08
You're describing an ethernet adapter but I think what you have is a wifi USB adapter. If I have this correct then try this link:-

[https://bbs.archlinux.org/viewtopic.php?id=149329](https://bbs.archlinux.org/viewtopic.php?id=149329)

but note that the link to the driver has changed to:-

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

from what I can see you need the driver at the top of the list.

Mark

---

### Post by Olipton on 2013-02-08
> **mapes12 said:**
> You're describing an ethernet adapter but I think what you have is a wifi USB adapter. If I have this correct then try this link:-

[https://bbs.archlinux.org/viewtopic.php?id=149329](https://bbs.archlinux.org/viewtopic.php?id=149329)

but note that the link to the driver has changed to:-

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

from what I can see you need the driver at the top of the list.

Mark

I'm working on all of this atm, if this works i will love you, no homo.

---

### Post by Olipton on 2013-02-08
> **Olipton said:**
> I'm working on all of this atm, if this works i will love you, no homo.

How do i actually dwonload the driver from your second link? I see nothing to click on.

Edit: nvm, got it.

---

### Post by Olipton on 2013-02-08
> **olipton said:**
> how do i actually dwonload the driver from your second link? I see nothing to click on.

Edit: Nvm, got it.

it works i love you

---

