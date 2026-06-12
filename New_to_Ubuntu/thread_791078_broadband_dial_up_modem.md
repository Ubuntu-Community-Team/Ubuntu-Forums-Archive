---
title: "broadband dial up modem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by koundinya on 2008-05-11
hi all
I configured my broadband dial up modem according to the instructions in the help in ubuntu 8.04 but in vain. My modem uses some ppoe to connect and requires username and password. does linux support ppoe modems if not where to get the required drivers??

---

### Post by seetho on 2008-05-11
Please specify the brand and model of your broadband modem (I suppose it is a DSL modem from your provider).  You may get more helpful replies then.

Most modems can login automatically for you so you don't have to use Ubuntu to dial.  Just connect and go (using the built-in dhcp).

---

### Post by koundinya on 2008-05-12
its ADSL2+ modem/router
other specifications are
company: UT Starcom
Model no.: UT300R2U
Hope this is enough Now pls tell me how to configure
also what is dhcp?? I have just installed ubuntu and started learning

---

### Post by seetho on 2008-05-12
> **koundinya said:**
> its ADSL2+ modem/router
other specifications are
company: UT Starcom
Model no.: UT300R2U
Hope this is enough Now pls tell me how to configure


It seems this modem is local only to your area. Many ppl should be using the same modem as you are.  The best would be to seek help from there for the correct settings.


> **koundinya said:**
> 
also what is dhcp?? I have just installed ubuntu and started learning

DHCP is a protocol to dynamically allocate a pool of IP number to connected hosts (your PCs). Just type dhcp on google and you get lots of information on this topic.  Modem/Routers usually come with a dhcp server built-in so when you connect your PC it automatically allocates you an IP number.  This is normally on by default for most units. However please check.  If this is a new modem that you have just bought then the manual should explain to you how you can configure it.  Otherwise just download it off the net.

Just try looking for answers by by yourself for a while.  You'll find that you learn more that way (and more satisfying).

Good luck.

---

### Post by koundinya on 2008-05-14
ya i configured the modem as per instructions in the manual. It worked on XP but not in ubuntu. Why is it so? 
Configuration of modem is same in any OS I think.

---

### Post by conscious on 2008-05-14
Maybe this will help you:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by seetho on 2008-05-14
> **koundinya said:**
> ya i configured the modem as per instructions in the manual. It worked on XP but not in ubuntu. Why is it so? 
Configuration of modem is same in any OS I think.

I suggest you set up your modem using your XP machine first.  Find out from your manual how to setup the modem to auto dial PPPoE - you have to key in your username and password once on the modem.

It should autodial and connect if you turn it on.  After that it does not matter whether you are using XP, Ubuntu, Mac, Solaris, BSD, .... etc.  Make sure you setup for dynamic IP network. Just plug in and you should be online.

---

### Post by nicedude on 2008-05-14
May I suggest that while this would be for in the future I would recomend you look into getting yourself a router. If you get a simple one it should be less than $50US, just make sure you get one that says it has "statefull packet inspection" as this is a hardware firewall to protect your home network. 

Everyone should have one simce it increases security as well as gives you 4 Ethernet ports to use with multiple computers at your home. I would suggest either Netgear or Linksys brands as they can handle your PPOE login for your network and let you use simple networking from ubuntu or windows machines without further complications.

heres a link to one at newegg for $39.99 with wireless that handles PPOE
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122016](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122016)

And heres a linksys on sale also for $39.99
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010)


Its well worth the money just turn off the wireless if you dont use it.

Hope it helps you out :-)

---

### Post by koundinya on 2008-05-14
hi seetho
I dont want to autodial at startup. I should be able to connect and disconnect to internet whenever I want. For this I dont want to switch on and off the modem each time because I disconnect net every 15 min while downloading to change my ip. According to the manual I followed the following steps
1. input [http://192.168.1.1](http://192.168.1.1) in the browser
2. Go to advanced setup menu and click on th WAN buton
3. Click on add to create a new configuration
4. Enter VPI and VCI values provided by ISP
5. Select connection type as PPPOE
6. Enter PPPoE username and password given by ISP
7 Save and reboot

After this I created a new connection by going to networks. I did the same in ubuntu. After the above 7 steps I created a connection as in the help but could not connect to net
@conscious
I have already done that since those are the same steps listed in the help menu in ubuntu OS
@nicedude
I cant afford 50$ at present

---

### Post by koundinya on 2008-05-14
hi
finally i got connected to net in ubuntu by repeating the same above mentioned steps how i dont know. However by typing poff net got disconnected.
and I could not connect to net again. In the help its given
to get connected pon dsl provider
to disconnect    poff dsl provider
What to type in place of dsl provider. I guess ISP name. I could disconnect just by typing poff but could not connect back by typing only pon. How to connect again??

---

### Post by billgoldberg on 2008-05-14
For the love of Xenu, get yourself a router.

Modems are hopelessly outdated and a router (wireless or not) gets you so much more options (home networking, multiple pc's on the internet, hardware firewall, ...). 

Not helpful at all, but still.

---

### Post by qamelian on 2008-05-14
> **billgoldberg said:**
> For the love of Xenu, get yourself a router.

Modems are hopelessly outdated and a router (wireless or not) gets you so much more options (home networking, multiple pc's on the internet, hardware firewall, ...). 

Not helpful at all, but still.
He already has a router. The UT300R2U is a combination ADSL modem and router. BTW, modems are not out-dated. Unless you have a direct pipe of some kind, you still require a modem to get on the 'net. A router is not going to get you connected to the internet by itself. Many routers now include a modem internally, but it is still a modem!

---

### Post by seetho on 2008-05-14
What koundinya has will work just fine.  It's a matter of setting it up correctly.  Check out the link given in one of the post about setting up pppoe.  I don't use it so I can't be of any help.

---

### Post by conscious on 2008-05-17
> **koundinya said:**
> hi
to get connected pon dsl provider

What to type in place of dsl provider. I guess ISP name. I could disconnect just by typing poff but could not connect back by typing only pon. How to connect again??
The argument of pon is the name of an options file located in /etc/ppp/peers. Just view that directory to get available options.

---

