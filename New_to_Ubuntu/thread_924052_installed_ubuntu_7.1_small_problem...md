---
title: "installed ubuntu 7.1 small problem.."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Avail on 2008-09-19
Hi gang.          edit: (normal wired adsl connection thru phoneline and lan cable) (fyi)

Im really noob to all this stuff and have tried to solve my problem by searching forums ect.. but with no such luck.

Recently installed Ubuntu 7.1 , very nice i love it to death but..
I have no idea why my internet connection doesnt work.
I have tried sudo pppoeconf , It says we have found 1-2 devices sorry but we couldnt get a response Rar rar Rarr. ;[. And yes the connection is very real. :P 

Need help. Any information will be GREAT. :>

---

### Post by Ripfox on 2008-09-19
Wireless? Wired? Dialup?

---

### Post by Avail on 2008-09-19
ADSL 256k  - wired .

---

### Post by Avail on 2008-09-19
Please , any information at all will help
I dont think its a driver issue because it recognizes eth0

---

### Post by Avail on 2008-09-19
Please forgive my ignorance . i know that what im saying makes no sense and may be a waste of time to a lot of you.
But lend a noob a hand... ive tried toying with the network settings , no luck so far... wondering if i need some sort of network card drivers

---

### Post by Tatty on 2008-09-19
Im afraid i have no experience with dial up networking in ubuntu, however you might want to look at

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

it looks a bit outdated, but it should hopefully get you there.

Did you try the network manager in the toolbar to see if that gives you any options?

---

### Post by Avail on 2008-09-19
Yes ive tried many combinations of network settings... It really sucks. ;[

That page is good thanks , but Its weird.. it detects eth0 (networkcard) , but it cant find the Access Concentrator... It would probably solve all my problems if that worked ;[

After using:  sodu pppoeconf   i get this message : 

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

/me prays someone knows how to fix this

---

### Post by Avail on 2008-09-19
/bump 

Wondering if its my ISP . Ive heard linux wont work with some ISP's. 
I will personally mail a Australian Football to anyone who can solve this. (can replace football with anything else :P )

$50 of value! to anyone lol

---

### Post by rustutzman on 2008-09-19
Did your ISP give you an IP number or is it set to use DHCP?

Russ

---

### Post by JKyleOKC on 2008-09-19
There are at least three different forms of network access in use by ISPs, so the starting point for you is to determine which of the three your ISP is using. The three are "static IP," "DHCP," and "PPPoE." 

Static IP means that the ISP assigns you an IP address and a gateway address, both in the form of four numbers separated by dots such as "192.168.0.1" (the numbers will each be 255 or less, since they represent 8-bit binary values). You have to enter these into the Network Manager and then access should be automatic. It's a one-time setup and subsequently you should not have to do anything to make the connection.

DHCP is a dynamic address assignment; the ISP's equipment detects that your modem has connected, and assigns an IP address and a gateway address automatically. This happens each time you power up the system, with no additional effort on your part.

PPPoE or "point to point protocol over ethernet" is also dynamic but the ISP equipment doesn't automatically detect your connection. Instead you have to log in with a User Name and password each time you power up. Upon accepting your login, the ISP assigns an IP address and a gateway address to use for that session. Some modems and routers do the login for you, once configured.

From your posting it sounds as if your ISP is using one of the last two, and the reference to an access concentrator indicates that for some reason the gateway address is not getting set automatically. This might be due to a problem at the ISP, or it could be a configuration problem at your end. Without more detail it's impossible to say...

---

### Post by Avail on 2008-09-20
Ok well , basically i can take out this lan cable (from this laptop im on now) and go BANG and switch it to another computer without touching a setting. So basically anything thats lannable (in my opinion , but im stupid) will connect straight away without me touching any settings. Just plug in the cable and it works. Im thinking this is DHCP.
But ive configured my ubuntu with dhcp and it dont work. 

Should i be using "Roaming mode" or should i be using "Automatic decection "

I have been trying Automatic detection because i think thats DHCP right?
I can run any kind of test you want , just explain how its done in la-mans terms.

---

### Post by rustutzman on 2008-09-20
It does sound like your ISP is setup for DHCP. Do you have the little monitor screens up by your panel clock? If you do and you do a right click on them what are your options? Does it list connection information?

Russ

---

### Post by bumanie on 2008-09-20
In 7.10 there was an issue for many that involved ipv6. To correct this, try below;
about:config in firefox address bar --> hit enter
in the filter type ipv6
right click on the line that appears and change the value form true to false. 

If that doesn't work you can you reverse the steps and put it back to how it was before.

---

