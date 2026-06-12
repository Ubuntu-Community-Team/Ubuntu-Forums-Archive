---
title: "Atheros ar9287 driver installed no wireless netword available"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2011-08-28
On a freshly installed alternate daily live 08/27/211, installation from the ar9287 worked perfectly, after reboot no wireless network are available.

ao@Port-AO-Oneiric:~$ dmesg | grep ath
[   14.525877] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.525906] ath9k 0000:07:00.0: setting latency timer to 64
[   14.616013] ath: EEPROM regdomain: 0x65
[   14.616019] ath: EEPROM indicates we should expect a direct regpair map
[   14.616029] ath: Country alpha2 being used: 00
[   14.616034] ath: Regpair used: 0x65
[   14.639518] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.641172] Registered led device: ath9k-phy0
 

Any idea?

Regards

---

### Post by buzzmandt on 2011-08-28
well not sure if this helps much but I also have ath9k and ran the same command, looks like the same results to me cept I'm using kubuntu which connects just fine.  could it be a prob with  network manager gnome and not so much the ath9k driver?


> buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ dmesg | grep ath
[   12.078765] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.078779] ath9k 0000:02:00.0: setting latency timer to 64
[   12.162468] ath: EEPROM regdomain: 0x69
[   12.162471] ath: EEPROM indicates we should expect a direct regpair map
[   12.162476] ath: Country alpha2 being used: 00
[   12.162478] ath: Regpair used: 0x69
[   12.169268] type=1400 audit(1314497938.830:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=698 comm="apparmor_parser"
[   12.171951] type=1400 audit(1314497938.840:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=698 comm="apparmor_parser"
[   12.255708] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.270531] Registered led device: ath9k-phy0
[   42.850669] type=1400 audit(1314497970.442:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=1658 comm="apparmor_parser"
[   42.853536] type=1400 audit(1314497970.442:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1658 comm="apparmor_parser"



what does ifconfig give you?
> buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:b7:d1:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

wlan0     Link encap:Ethernet  HWaddr c4:17:fe:2c:e9:eb  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fe2c:e9eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1161518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:643253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1698029741 (1.6 GB)  TX bytes:60256385 (60.2 MB)


---

### Post by Yahoé on 2011-08-28
> **buzzmandt said:**
> well not sure if this helps much but I also have ath9k and ran the same command, looks like the same results to me cept I'm using kubuntu which connects just fine.  could it be a prob with  network manager gnome and not so much the ath9k driver?





what does ifconfig give you?

Could be:
ao@Port-AO-Oneiric:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:bc:2c:c2  
          inet adr:192.168.1.2  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::1e75:8ff:febc:2cc2/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:147377 erreurs:0 :0 overruns:0 frame:0
          TX packets:94237 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000 
          Octets reçus:212233058 (212.2 MB) Octets transmis:7564657 (7.5 MB)
          Interruption:42 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:65:55:31  
          inet adr:192.168.2.100  Bcast:192.168.2.255  Masque:255.255.255.0
          adr inet6: fe80::8a9f:faff:fe65:5531/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:458 erreurs:0 :0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:165703 (165.7 KB) Octets transmis:12105 (12.1 KB)

---

### Post by buzzmandt on 2011-08-28
that tells me your wireless is actually working and by the looks it is connected to what looks like might be a router.  There are several posts here about wireless not working, i'm starting to think it's a network manager gnome issue.

I have 3 different laptops running ath9k all with kubuntu oneiric and no issues at all.  maybe someone else might have a little more to offer than i do and can help you more.  I've seen threads on how to connect wireless through terminal, dunno if that might help you too

---

