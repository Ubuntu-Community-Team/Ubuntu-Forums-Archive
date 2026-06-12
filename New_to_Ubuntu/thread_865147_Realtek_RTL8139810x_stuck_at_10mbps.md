---
title: "Realtek RTL8139/810x stuck at 10mbps"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by zeasar on 2008-07-20
Hi guys, I have recently d/led ubuntu 8.04 and now dual booting with my re-installed windows XP.

Previously my pc was running XP home only and I can get 100mbps connection with my router via ethernet cable. After I tried ubuntu and decided to do dual booting, I wiped my HD and reinstalled XP and then installed ubuntu. Now both XP and ubuntu can only connect to the same router via the same ethernet cable on 10mbps.

In XP I tried to change the connection from autonegotiate to 100mbps full-duplex, It connects for about 2 sec and then a msg box poped up saying the network cable is unplugged. I have to set it to 10mbps or autonegotiate to get the network connected.

BTW my network cards driver on XP is up-to-date.

Thanks in advance for any help or advice :)

---

### Post by pavel989 on 2008-07-20
could be your router. and have u actually noticed a difference?

---

### Post by zeasar on 2008-07-20
I have a Macbook connected to the same router with ethernet cable, and when I use the mac to access some files on the PC it feels much slower.

BTW, more info, mac is connected to the same router at 100mbps, ubuntu is fully updated, XP isnt (didnt want to update since microsoft wants me to install "genuine advantage" update -_-).

Router is Linksys WAG54GS.

---

### Post by pavel989 on 2008-07-20
hm. im somehow leaning towards saying its the router but dunno. dats weird.

---

### Post by zeasar on 2008-07-20
Yea, pretty weird.

Could a static ip be the cause? For some reason ubuntu always log on the router with the ip 192.168.1.104 (skipping 1.100, 1.101, 1.102, 1.103) and my XP is statically set to the ip 192.168.1.109

Since they are on the same PC and the same network card, does 2 different ip cause any conflicts?

---

### Post by pavel989 on 2008-07-20
it should be using the same IP bc its the same mac address. what does ur mac do?

---

### Post by zeasar on 2008-07-20
> **pavel989 said:**
> it should be using the same IP bc its the same mac address. what does ur mac do?

Erm, my mac is on a static ip address as well, and it's connection isnt affected at all.

Anyways, now to boot up the pc and change the ip settings.

---

