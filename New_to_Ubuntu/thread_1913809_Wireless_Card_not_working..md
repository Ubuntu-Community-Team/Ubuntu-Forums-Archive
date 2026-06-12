---
title: "Wireless Card not working."
date: 2012-01-23
forum: New to Ubuntu
---

### Post by chris1neji on 2012-01-23
Hello it's me again this time on one of my friends computer. This is his laptop he plans to use it for browsing and word.

Anyways the sound works, and so do other things however the wireless card doesnt.

The physical wireless key switch itself wont turn on usually orange when disable and blue when enable.

This is a Compaq Presario v5000

I am using Lubunto 11.10

please help

it's 3 am almost so i am off to bed i have classes in a few hours

update

read a quick post on how to get help faster


juan@juan-Presario-V5000-RG324UA-ABA:~$ lspci | grep Wireless
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Nick_Kats on 2012-01-23
Can you please run lspci and lsmod on your terminal and post the results here.

---

### Post by sandyd on 2012-01-23
> **chris1neji said:**
> Hello it's me again this time on one of my friends computer. This is his laptop he plans to use it for browsing and word.

Anyways the sound works, and so do other things however the wireless card doesnt.

The physical wireless key switch itself wont turn on usually orange when disable and blue when enable.

This is a Compaq Presario v5000

I am using Lubunto 11.10

please help

it's 3 am almost so i am off to bed i have classes in a few hours

update

read a quick post on how to get help faster


juan@juan-Presario-V5000-RG324UA-ABA:~$ lspci | grep Wireless
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Connect to your LAN (wired).
```

sudo apt-get install firmware-b43-installer dkms
```

---

### Post by chris1neji on 2012-01-23
thank you :)

---

