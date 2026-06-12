---
title: "no driver for eth0"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by jrev on 2011-11-30
I just installed ubuntu 10.04 on a PC with Win07.
the transmission through eth0 is OK on Windows and doesnt work on Ubuntu.
How to find the proper driver ?
Thanks for your help

---

### Post by roger_1960 on 2011-11-30
Hi

What ethernet hardware is it?

can you run 

```
sudo lshw
```

and post the result

Have you tried: system settings>hardware>additional drivers ?

---

### Post by jrev on 2011-12-01
aucun pilote propriétaire n'est utilisé sur ce PC

jean@jean:~$ lspci -nn | grep -i net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
08:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
jean@jean:~$

jean@jean:~$ sudo lshw -C network
[sudo] password for jean:
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:83:cb:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.20 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:2b:e8:9d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.0.21 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d1000000-d103ffff ioport:2000(size=128)
jean@jean:~$

Mal nommer les choses, c'est ajouter au malheur du monde

En ligne

    * Signaler aux modérateurs
    * Supprimer
    * Modifier
    * Citer

#4 Hier à 18:19

jrev

Re : ethO non reconnu

jean@jean:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:2b:e8:9d 
          inet adr:192.168.0.21  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::226:22ff:fe2b:e89d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1822 erreurs:0 :0 overruns:0 frame:0
          TX packets:1438 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000
          Octets reçus:2008778 (2.0 MB) Octets transmis:183392 (183.3 KB)
          Interruption:27

lo        Link encap:Boucle locale 
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:12 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:720 (720.0 B) Octets transmis:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:83:cb:52 
          inet adr:192.168.0.20  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::e60:76ff:fe83:cb52/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4 erreurs:0 :0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:997 (997.0 B) Octets transmis:4398 (4.3 KB)

jean@jean:~$

Mal nommer les choses, c'est ajouter au malheur du monde

En ligne

    * Signaler aux modérateurs
    * Supprimer
    * Modifier
    * Citer

#5 Hier à 18:22

jrev

Re : ethO non reconnu

je précise que mon eth0 fonctionne sous Windows en doublure sur ce PC

---

### Post by 3rdalbum on 2011-12-01
Ubuntu 10.04 is fairly old. There have been three versions released since 10.04.

I'd suggest you try 11.10 and see if it works there. From my very quick research it appears that the card doesn't work with distros released around the time 10.04 was released.

---

### Post by Jacobonbuntu on 2011-12-01
...indeed! I don't know exactly from which kernel version it was supported, but it was since an update during 11.04. 11.10 should work.

---

### Post by jrev on 2011-12-01
How can I cut the wifi connection to the  FAI on Windows7 on my laptop ? 
in order to test the Eth0 connection ?

Thanks
When I try with the live-CD Slitaz I have no connection at all ...
Usually I have a wired cnnexion available 
Thanks for your guidance

---

### Post by roger_1960 on 2011-12-01
Hi

Those drivers - eth0 and wlan are supported in 11.10  You could try a live 11.10 USB and see if it works then.

Otherwise, could windows be switching off the wired  ethO port and leaving it closed when it shuts down?  I have had this problem once before.  TRy shutting down windows with the wired lan on.  Most laptops have a hardware switch or key combination FN+F? for turning off the wifi radio.

---

