---
title: "How to find out if I can use wireless on a used laptop?"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by loro123 on 2013-10-02
Hi, I installed lubuntu 13.04 on an old laptop I bought. Now I want to use wireless, but I don't know how to find out if the laptop is even able to do wireless.

I searched around and I am supposed to type "lshw -C network" into terminal, but I don't understand the output. I also don't know how to change the output language to English, sorry (if that's possible).

>   *-network               
       Beschreibung: Ethernet interface
       Produkt: DP83815 (MacPhyter) Ethernet Controller
       Hersteller: National Semiconductor Corporation
       Physische ID: c
       Bus-Informationen: pci@0000:02:0c.0
       Logischer Name: eth0
       Version: 00
       Seriennummer: 00:03:0d:14:42:ec
       Größe: 100Mbit/s
       Kapazität: 100Mbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=10.0.0.2 latency=64 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       Ressourcen: irq:17 ioport:c800(Größe=256) memory:dfefe000-dfefefff memory:dfee0000-dfeeffff




What do I do now?

---

### Post by Bucky Ball on 2013-10-02
That machine doesn't have wireless. You would see the details for 'Network Controller' if it did. ;(

Dongles are cheap now and lots work on Ubuntu.

---

### Post by Bucky Ball on 2013-10-02
Welcome. That machine doesn't have wireless. You would see the details for 'Network Controller' as well as 'Ethernet Controller' if it did. ;(

USB Dongles are cheap now and lots work on Ubuntu.

---

