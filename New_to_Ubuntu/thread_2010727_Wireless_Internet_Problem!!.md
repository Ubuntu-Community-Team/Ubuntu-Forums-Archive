---
title: "Wireless Internet Problem!!"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by atadkase on 2012-06-26
Well,I installed Lubuntu 12.04 on my really old system.It has a Belkin G Usb Wireless adapter to connect to my home wireless.My setup for wireless runs as follows:-
1.I've a DSL modem which connect AUTOMATICALLY to the ISP.
2.The DSL modem is connected to a wireless router by CAT5 cable.
3.The router connects to my computers by wifi.(one win7 laptop,the other-the really old pc)
_**Note:-BOTH the router and the modem have the SAME IP address i.e.192.168.1.1(for convenience,i tried changing but the internet doesnt work!).**_
Now from Lubuntu,I can connect to wireless router,access its CP but not the DSL modem,whereas on XP(which runs on same ole comp) I can access only the DSL modem(which is preferable).So thats why i cant connect to internet.Any fixes?? I am unable to see the other computers on network on both PCs and am unable to ping any website.Any help would be really appreciated(i really dont want to switch back to xp(it laggs a lot!)).](*,)

---

### Post by cariboo on 2012-06-26
It sounds as if the problem is caused by the router and the modem having the same ip address. When you changed the router ip address, what did you change it to? THey both have to be in the same netblock, so I'd suggest leaving the modem ip address as it is, the change your router ip address to:

```
192.168.1.2
```

I have a cable modem, that I can't access directly, but I do use two routers, their ip addresses are:

[LIST]
[*]local router 192.168.1.1
[*]remote router 192.168.1.2
[/LIST]

The remote router is in my shop, attached to the the local router via a 50 meter long cat5 cable.

---

### Post by UltimateCat on 2012-06-26
Your Belkin adapter may need a driver to aid it.  And your network interface may need the same; it's hard to tell.

You mentioned that your PC is really old; the make and model may help us to help you.  What kind/brand Desktop Pc do you have?

Try opening the Terminal and post the results to this command it helps to see PCI buses and to be able to diagnose problems.

To open a terminal type and hold down  Ctrl +Alt+T

```
lspci

```

[www.belkin.com](www.belkin.com)

---

### Post by atadkase on 2012-06-26
Well, I changed the IP address of the router to 192.168.1.2.The internet still works for my laptop,but still its the same problem for Lubuntu.:confused:
My PC is an assembled one,has a celeron 2ghz(doesnt provide that much speed),ram 2 sticks-256mb and 128mb,no graphics card.

And the result for lspci:-
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:05.0 Bridge: LSI Corporation 56k WinModem (rev 01)
03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by marinara on 2012-06-26
what model of router do you have exactly?

---

### Post by atadkase on 2012-06-26
The router is one UTSTARCOM WA3002G1 model(about 6 yo).

---

### Post by marinara on 2012-06-27
that's a router-modem.
most likely your router-modem isn't routing anything, but only acting as a hub.  I can explain the diff. if you desire.

---

### Post by atadkase on 2012-06-28
I solved the problem by doing the following:-
1.Installing Ubuntu 10.04
2.Changing the router ip to 192.168.1.2
3.Giving both the computers static ips and dns.
4.Changing router settings to route the comps to the modem.
Well,thats all folks!!:popcorn:):P

---

