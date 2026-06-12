---
title: "How to enable/make/run a static IP on my laptop"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by lewis4 on 2014-05-29
Hello,

I've been developing a Modded Minecraft Server for public & a FTP file server use on Linux Ubuntu 14 for quite some time. A few days ago I tried to enable/make/run a static ip off my Linux Laptop, and it does not seem to be working. I have read a few tutorials & forum threads about it but they don't seem to be helping me. Can you guys tell me how to run/make/enable a Static Ip address on my laptop as I'm am a little depressed that it did not work. 

Thank you!

---

### Post by jdeca57 on 2014-05-29
As an example on a lan and with the unity GUI you have the right upper menu the network connection where you can edit connections. Use you connection, set IPV4 manual instead of DHCP, and enter the address you want to use (like 192.168.1.200), subnet mask (255.255.255.0) and  gateway and DNS server. The last are probably the address of the router you use, like 192.168.1.1. That works and is consistent - remains after boot.

---

### Post by lewis4 on 2014-05-29
I have tried that put my Ip that I give out to players keeps on changing everyday, are you able to give me a more in-depth description?

---

### Post by jdeca57 on 2014-05-29
Well, actually your provider changes addresses in order to prevent you from doing what you want, with other words you don't have a static IP. There are ways around this, look at [www.noip.com](www.noip.com) as an example.

---

### Post by kyle20 on 2014-05-29
You will need to contact your ISP, and request a static IP. Typically this will cost a decent amount of money, but it's the only way to ensure that your IP does not change.

---

### Post by lewis4 on 2014-05-29
So will I be able to hook my IPV4 address onto a domain name with this website?

---

### Post by jdeca57 on 2014-05-29
> **lewis4 said:**
> So will I be able to hook my IPV4 address onto a domain name with this website?

Some years ago I made a similar setup. Yes, in theory you can have a stable connection with a changing (dynamic) IP. But it's more a website or mail approach, not a gaming situation. After the IP changes there is a transition / update time. That might annoy users. ;-) The best (professional) way to go is - as mentioned - to purchase a static IP.

---

### Post by lewis4 on 2014-05-29
Okkie Dokkie thanks!

---

### Post by CaptainMark on 2014-05-29
no-ip should be adequate for most non-enterprise purposes and can be easily configured to be updated from either a home router (most but not all will be compatible) or to be updated straight from more or less any linux desktop/laptop/server

---

