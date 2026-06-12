---
title: "New ISP, how to connect to the Internet"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by hunter551 on 2008-09-10
I have changed ISPs which resulted in a change of modem. After setting up the dsl modem in windows xp, with the internet working fine, when i boot into ubuntu the internet does not connect.

I never had to setup the internet before because when i installed ubuntu it was already connected.

How can i get ubuntu to connect to the modem without changing any of the modems settings/configurations?

---

### Post by Kinetic_lord on 2008-09-10
What modem do you have? Is it a speed touch 330?

---

### Post by skippuff54 on 2008-09-10
how r u connectin the ubuntu box to the modem? what else is on ur network (other computers, routers, hubs)? i dunno about dsl, i use cable but maybe i can help...

also do u know if u have to pay extra for additional IP addresses?

---

### Post by iaculallad on 2008-09-10
Try this on your terminal:

```
sudo dhclient -r
sudo dhclient
sudo /etc/init.d/networking restart
```

Then:

```
ping ubuntuforums.org
```

---

### Post by Kinetic_lord on 2008-09-10
I have Speed Touch 330 drivers... answer is this is you're modem

---

### Post by hunter551 on 2008-09-10
My Modem is a speedstream 4200.

I'm connecting it via ethernet cable. This is the only computer using it.

---

### Post by skippuff54 on 2008-09-10
sounds like it has to do directly with ubuntu recognizing ur ethernet card as its network interface. maybe u need to install a driver for ur card. or just tell ubuntu to use ur card as its primary network interface.

what happens when u type ```
sudo ifconfig
``` in a terminal? u should see somethin like eth0 listed as ur network interface. it should also be listed under ur system > network dropdown menu

---

### Post by hunter551 on 2008-09-10
Doing what iaculallad suggested did not help.

Typing in sudo ifconfig i do get eth0 plus something else which i assume is my dial-up modem.

---

### Post by skippuff54 on 2008-09-10
does it say if eth0 is gettin an IP address? another listing might be sit0, which is your local loopback interface (which u don't exactly need to worry about for gettin internet)

---

### Post by hunter551 on 2008-09-10
I've tried typing in the IP addresse of the modem (it comes up with configuration settings in windows) but it says it cannot find the server.

---

### Post by skippuff54 on 2008-09-10
are you dual-booting?

when you type sudo ifconfig in terminal, and you see eth0, what all does it say? will u post what it says there?

it sounds like ubuntu recognizes that you have the card installed and all just fine, but it doesn't know to use it for your internet connection. it needs to recognize eth0 as your primary network interface.

have u tried to power cycle the dsl modem before u boot into ubuntu? have u looked at all ur network config options in ubuntu?

---

### Post by skippuff54 on 2008-09-10
also ur card/network settings need to obtain an IP address automatically from the DHCP server

---

### Post by hunter551 on 2008-09-10
Yes i am dual-booting. How would I check that setting?
I'll post the output of that when i boot into ubuntu.

---

### Post by Kinetic_lord on 2008-09-10
[https://help.ubuntu.com/community/DialupModemHowto?action=fullsearch&context=180&value=speed+stream+4200+drivers&fullsearch=Text#Download%20/%20Detect%20and%20Configure%20/%20Install](https://help.ubuntu.com/community/DialupModemHowto?action=fullsearch&context=180&value=speed+stream+4200+drivers&fullsearch=Text#Download%20/%20Detect%20and%20Configure%20/%20Install)

Look here... i hope it's dialup modem...

---

### Post by hunter551 on 2008-09-10
Its not dialup.

here's the output, i've blanked out some of the numbers.

eth0      Link encap:Ethernet  HWaddr 00:11:5b:**:b8:07  
          inet addr:58.107.**.**  Bcast:58.107.**.255  Mask:255.255.255.0
          inet6 addr: fe80::***:5bff:fed5:b807/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:590 (590.0 B)  TX bytes:4953 (4.8 KB)
          Interrupt:20 Base address:0xb000

---

### Post by billgoldberg on 2008-09-10
Get a router. 

Modems are a thing from the past.

You can set up your ISP internet  connection from the routers webinterface then.

---

### Post by hunter551 on 2008-09-11
There should be a way to get this to work, it worked before with the exact same model.

---

### Post by skippuff54 on 2008-09-11
post ur /etc/network/interfaces file...open with a text editor

you have to make sure that ur ethernet card, not ur dial-up modem, is ur primary network interface

---

### Post by hunter551 on 2008-09-12
ok, after switching the dsl modem with a netgear wireless router it worked. I didn't have to set anything up, it just worked when i booted into ubuntu.

---

### Post by skippuff54 on 2008-09-12
the rest of the network works too? can u describe ur network now, for others? any idea what ur router is doin for u that wasn't bein accomplished previously?

workin from behind the router is preferable anyways. now u have a firewall, and u'll probably find settin up ur network to be a little easier.

---

### Post by hunter551 on 2008-09-12
Well at the moment i've got the adsl phone line going straight into a netgear DG834G. Then i've got a network cable going from that into my computers network adapter. I've got no idea why this works and the other one didn't though.

---

