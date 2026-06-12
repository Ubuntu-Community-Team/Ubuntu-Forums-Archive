---
title: "Wireless just stopped"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-07-19
The wireless connection hs just gone on my ubuntu computer - 
I was wondering if anyone could help me?

It not out of range - because I was just using it
Its not the internet in general - because im on the same wireless now
Its not anything I think I've done - but I'm happy to stand corrected

So when I reboot - the green icon spins in the conrner telling me it's trying to connect - then I get 2 computer screens with a exclamation mark - 

if I left click - I get the option to connect to my usual internet connection (which seems to have singnal since there is a half full signal bar beside its name), if I click it - it just fails to connect

if i right click i get the option to connect to another network or configure my network - I have tried changing my current connection to a static IP and disable Roming mode - but neither work

I have rebooted and the same - oh and my hardware driver is still there under 'hardware drivers' ...

I'm at a loss. Any help would be greatly aphresiated.

Thanks guys

---

### Post by phantomjoker on 2008-07-19
Oh - and I tried 

```
Network-admin --help
```

but it doesn't really help - hence I need you guys

cheers

---

### Post by braddcadd on 2008-07-19
(1) Is it possible you are missing the WEP or WPA key in your configuration?

(2) Are you using DHCP?

(3) Post results of the following commands:
```

ifconfig

```
(see if you can determine which one is the wireless card, on my computer it is wlan0)
```

iwlist scan wlan0

```
```

sudo dhclient wlan0

```

---

### Post by phantomjoker on 2008-07-20
```

wlan0     Link encap:Ethernet  HWaddr 00:11:50:0b:60:39  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe0b:6039/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7000317 (6.6 MB)  TX bytes:1787899 (1.7 MB)
```

this is the readout

---

### Post by phantomjoker on 2008-07-20
but its ok now thanks - I managed to fix it - hardware problems...
cheers

---

