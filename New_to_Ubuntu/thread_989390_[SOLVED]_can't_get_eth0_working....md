---
title: "[SOLVED] can't get eth0 working..."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by junkfixer on 2008-11-21
I have just installed 8.10 for the second time and it did not install my network adapter. I looked in /etc/network/interfaces and all it lists is:
auto lo
iface lo inet loopback
I believe there should be something else there related to eth0... can someone help me?

---

### Post by drakeman007 on 2008-11-21
> **junkfixer said:**
> I have just installed 8.10 for the second time and it did not install my network adapter. I looked in /etc/network/interfaces and all it lists is:
auto lo
iface lo inet loopback
I believe there should be something else there related to eth0... can someone help me?

The network manager dont work for you?
dhcp or static ip?

---

### Post by Kevbert on 2008-11-21
What do you get with
```
ifconfig
lspci
```

---

### Post by junkfixer on 2008-11-21
I'm using dhcp...

(bare with me, I can't cut and paste, the install is on another machine, and I have no internet because I have no LAN on that machine...)

ifconfig gave me:   
eth0    Link encap:Ethernet  HWaddr 00:40:33:e3:7b:ee
        UP BROADCAST MULTICAST  MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collissions:0 txqueuenlen:1000
        RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        Interrupt:10 base address:0xe800

and then the "lo" information...

and lspci shows all the divices in my box including:
      00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

so I think that means it recognizes my equipment...?

---

### Post by bodhi.zazen on 2008-11-21
And what happens if you :

```
sudo dhclient eth0
```

---

### Post by junkfixer on 2008-11-21
I get:

Listening on LPF/eth0/00.40.33.e3.7b.ee
Sending on   LPF/eth0/00.40.33.e3.7b.ee
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inerval 4
"                                                     " 5
"                                                     " 10
"                                                     " 7
"                                                     " 19
"                                                     " 15
"                                                     " 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by bodhi.zazen on 2008-11-21
Not sure, but start with the "easy" stuff : is your router working, loose cables anywhere ?

---

### Post by Kevbert on 2008-11-22
If you need to copy any output from terminal. You can 'pipe' the information to a file with '>' e.g.
```
lspci > data.txt
```
This will save the output of lspci to a file called data.txt in your current folder (normally your home directory).
By the look of it your wired lan has been detected.

---

### Post by junkfixer on 2008-11-22
!SOLVED!

I really didn't think that setting up a network card in Ubuntu would be very difficult, and it ISN'T! when you use a fully functional interface card?!?! The Realtek card wasn't working and I tried an ISA card and it didn't show up at all on the "lspci" output, so I kinda figured that Ubuntu doesn't support the ISA bus...? So I borrowed a PCI card from another machine and VOILA' it worked! 

Now I just have to figure out how to show the files in my windows shares.

But many thanks to kevbert, bodhi.zazen and drakeman007 for your help, I'm very pleased to be a new part of this community and I hope to be of help to someone else soon. -Tony

---

