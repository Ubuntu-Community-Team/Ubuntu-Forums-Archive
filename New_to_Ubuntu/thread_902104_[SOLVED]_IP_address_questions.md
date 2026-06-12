---
title: "[SOLVED] IP address questions"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-27
Hi.  I have a question about IP addresses.  It seems that different sources are giving me different IP addresses for the same machine.

ifconfig gives me 192.168.1.104 as assigned by my router

nslookup hostname gives me 

Server:		24.92.226.40
Address:	24.92.226.40#53

Non-authoritative answer:
Name:	hostname
Address: 24.28.193.9

not sure what to make of that. . .

Finally, [http://whatismyipaddress.com/](http://whatismyipaddress.com/) gives me:
24.59.196.196

Why is it that I have three IP addresses?  I am pretty good with Ubuntu and Linux, but I'm a networking noob. . . 

Thanks in advance!

---

### Post by perlluver on 2008-08-27
> **pi.boy.travis said:**
> Hi.  I have a question about IP addresses.  It seems that different sources are giving me different IP addresses for the same machine.

ifconfig gives me 192.168.1.104 as assigned by my router

nslookup hostname gives me 

Server:		24.92.226.40
Address:	24.92.226.40#53

Non-authoritative answer:
Name:	hostname
Address: 24.28.193.9

not sure what to make of that. . .

Finally, [http://whatismyipaddress.com/](http://whatismyipaddress.com/) gives me:
24.59.196.196

Why is it that I have three IP addresses?  I am pretty good with Ubuntu and Linux, but I'm a networking noob. . . 

Thanks in advance!

ifconfig is your local network address.  Whatismyip.com, is your world IP.  Not sure about the server address.

---

### Post by pi.boy.travis on 2008-08-27
> **perlluver said:**
> ifconfig is your local network address.  Whatismyip.com, is your world IP.  Not sure about the server address.

OK, so I really have two IP addresses.  What command can I use to find my "world IP address?"

Thanks!

---

### Post by cariboo on 2008-08-27
Your server address is your isp's dns server

> Finally, [http://whatismyipaddress.com/](http://whatismyipaddress.com/) gives me:
24.59.196.196

Your world readable address is the same as the qouted.

Jim

---

### Post by perlluver on 2008-08-27
> **pi.boy.travis said:**
> OK, so I really have two IP addresses.  What command can I use to find my "world IP address?"

Thanks!

whatismyip.com, will give you the world IP.  So > Finally, [http://whatismyipaddress.com/](http://whatismyipaddress.com/) gives me:
24.59.196.196 that is your world ip.

---

### Post by pi.boy.travis on 2008-08-27
> **cariboo907 said:**
> Your server address is your isp's dns server

Jim

> **perlluver said:**
> whatismyip.com, will give you the world IP.  So


OK, thanks cariboo907.

Is there a terminal command I can use to find my world IP?

Thanks!

---

### Post by sisco311 on 2008-08-27
> **pi.boy.travis said:**
> OK, thanks cariboo907.

Is there a terminal command I can use to find my world IP?

Thanks!
[http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html](http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html)[URL="http://ubuntuforums.org/echo%20"]
[/URL]

---

### Post by pi.boy.travis on 2008-08-27
> **sisco311 said:**
> [http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html](http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html)[URL="http://ubuntuforums.org/echo%20"]
[/URL]

EXACTLY what I was looking for!  Thanks!

---

### Post by cariboo on 2008-08-27
I can't find a command line utlity to find your world readable ip address, but there are a lot of other resources.

1. If you are using a router access your router's admin interface
2. [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

I'm sure there are a lot more sites that will tell what your ip address is.

Jim

---

### Post by cocokiwi on 2008-08-27
> **pi.boy.travis said:**
> Hi.  I have a question about IP addresses.  It seems that different sources are giving me different IP addresses for the same machine.

ifconfig gives me 192.168.1.104 as assigned by my router

nslookup hostname gives me 

Server:		24.92.226.40
Address:	24.92.226.40#53

Non-authoritative answer:
Name:	hostname
Address: 24.28.193.9

not sure what to make of that. . .Well get out the popcorn:popcorn:pullup a chair,turn on the :guitar:and I,ll try to enlighten you!:confused:


Ok! the 192.168.1.104 is your computer..your kid's computer if you had one could be 192.168.1.105..any # 192.168.0 to 255.0 to 255 can be used in a home network. you can use all sorts of configuration's as you can put all sorts of things on the network these days.

ok! 192.168.1.0 computer-----[router(192.168.1.1)--
---192.168.1.4(network printer)----(192.168.1.5)computer 2.

from router(192.168.1.1)--<---(24.28.193.9)internet(from Modem)to Router only/connection to > 192.168.0.124 (HDTV streaming) from HDTV box to any computer or HDTV Network device.etc! 4 connections..HUB if more!

you use the IP addresses as a means to link different things by using different IP setups
192.168 (base settings)
.1.x  = computers on network!  0.x could be Printer network(allows one to put a printer anywhere you want it and access it from any computer)

Even a laptop, if of course you have a WI-FI link,you can add it as a stand alone or get it as part of the router,the newer ones support the NEW N mode!
A = 5gig(business mostly)fast! B was the ORG version 12 meg/G is 54 gig and N = 100 meg +..all usualy suppot ALL modes,unless it,s an older unit,
most HP laptops and others these days support all modes..handy if you cannot run wires around the house but need to access upstairs!how do you do it?

downstairs setup a router/wi-fi..you have 4 network cable connections!
computers/HDTV/Printer(downstairs)

Upstairs setup another Router/Wi-fi as a BRIDGE between floors,as downstairs you have 4 connections for 4 devices upstairs,if you need more you add a HUB with more connections,they come with 4 to 16 connections!not that you need that many(grin) Hubs come in differnt speeds  10/100 is the most common 1 gig and above is newer and needs a slightly faster cable to work right CAT-5 is the common one/CAT-5-e is the 1 gig size..you do NOT staple these cables as one will do with a phone line,use a staple,then poke a small tiewrap through the staple and tie the wire to it,the reason is crimping the cable affects it's signal and can cause some problems in the link!

From the router one would run a cable to each bedroom upstairs! in each bedroom a hub(4 connections) would connect whatever devices you had to connect!NOW! backing up here! just in case! 
If you run into the problem where you rent the place and you CANNOT run wires(grin) more expensive,but can be done!I have a ASUS M2N32-SLI amd AM-2 deluxe WI-FI..has a plugin wifi card and TWO LAN conections(very nice Motherboard)now you can use a BRIDGE unit upstairs(not a router)it is only a link and the same or router..the computer downstairs LAN would be connected to a router/internet device/the other lan would connect to a HUB...as before! all done without wires! if you have computers without WI-fi cards you can buy them and plug em in,IF you have SPACE!
Yes! if you have TWO video cards in a SLI configuration,you then have another problem if you have another card using the ONLY PCI slot left(grin) as the Video card COVERS the OTHER slot!and now they have 3 video card slots! FUN! (there is an Intel version of the 
Wi-fi card Deluxe board) I,m just covering the bases here and covering MOSt of the problems you may have if you setup a network,I hope I have kept it so you can understand it(grin):lolflag:

it,s the way IP,s are configured on a Private network! if you have a ROUTER and you are running DHCP which is a AUTO means of setting up IP address's Automaticly,you set it up as a GATEWAY,a link to other area's EG..Internet

Common IP gateway for the Router is 192.168.1.1 and is a common problem with networks when you cannot SEE the internet,usualy the Gateway is not setup or has gliched and bumped it!  

The other one is your Provider... the fist # is the Main IP and the second is the backup is the first one fails!:confused:Still??

Finally, [http://whatismyipaddress.com/](http://whatismyipaddress.com/) gives me:
24.59.196.196

Why is it that I have three IP addresses?  I am pretty good with Ubuntu and Linux, but I'm a networking noob. . . Think you do now!:confused:

Thanks in advance!:lolflag:

Cheers! Dennis

---

