---
title: "Need Help: Sharing Internet Connection using USB Modem"
date: 2009-09-07
forum: Philippine Team
---

### Post by killer_d76 on 2009-09-07
Guys.. patulong naman oh.. I'm using a **Huawei E160 USB modem** (Sun Cellular) and I have a **TP-Link Wireless Router**.. the USB modem is connected to one of the USB port and the Wireless Router is connected thru ethernet port, we have another laptop that we would like to connect to internet thru wireless router.. after a few search on the net i found this simple solution.. just configure the **eth0 IPV4 settings** to **"shared to other computers"**.. but it seems like its not working at all... patulong naman po o.. ;)

thanks in advance.

---

### Post by kiminaiseah on 2009-09-07
i was done it before by masq or setting up a squid,
i think yung tp-link mo na router ang wan interface nya point sa pc mo pero medyo mabagal kasi violation of rfc1918 wan interface should have no route with 192.0.0.0 10.0.0.0 172.0.0.0 etc... pupunuin ng logs ang router mo saka pati yung syslog ng linux mo hehehe

---

### Post by pinoyskull on 2009-09-08
If you have the money, just buy a 3G Broadband router, around 3-4K lang to
[http://edimax.com/en/produce_detail.php?pd_id=279&pl1_id=3&pl2_id=18](http://edimax.com/en/produce_detail.php?pd_id=279&pl1_id=3&pl2_id=18)

---

### Post by killer_d76 on 2009-09-08
ouch!... hehehe unfortunately i don't have the fortune to buy an additional gadget for now ;) although I was able to share my USB internet connection using Mac with a few simple steps.. if you would like to know how i did it.. PM me na lang hehehe, though I still prefer using Ubuntu specially **#!** hhaaayyyy..

---

### Post by perbiu on 2009-09-09
Try installing Firestarter, it has an easy wizard which you can share your internet.

---

### Post by killer_d76 on 2009-09-09
thakns perbiu.. will try that later!.. ;)

---

### Post by exkludge on 2009-09-24
@killer_d76

ndi ko sigurado kung tama pagkakaintindi ko sa setup mo ha.. ganito ba?

(usb modem) <----> (ubuntu pc) <----> (tp-link router) <----> (laptop)

sa WAN port ba ng tp-link router mo ikinabit yung UTP cable mo na galing sa Ubutnu PC?

---

### Post by killer_d76 on 2009-09-24
exkludge, ganito yung set-up ko bossing..

The Sun Cellular USB modem is plugged in at one of the USB port on my Ubuntu Laptop, on the ethernet port I have plugged in an ethernet cord (Cat5) going to the WAN port of the TP Link Router (not on the other port with designated numbers where you usually plug-in a non-wireless computer such as Desktop)

  Sun BB USB modem > USB*Ubuntu Laptop*ethernet > TP Link
(Internet Provider)       (Server)               (Router)


on Mac OSX it has a feature called **"Internet Sharing"** wherein my Laptop become a **Server** and a **Router** **at the same time**!.. I don't need to add or connect an additional device such as the  TP Link Wireless Router to share my internet connection coming from my USB Modem, this is very handy if I wanted to share my internet connection to my friend or colleague if we wanter to go on-line at the same on any given location! astig!..

May ganito bang feature/program sa Ubuntu?.. I would still prefer to use Ubuntu rather than OSX :guitar:



SideTrack: check out my Beans! **666** hehehe :D

---

### Post by Script Warlock on 2009-09-24
sa 8.04 wala akong problema sa ics pero etong 9.04 kahit na nilagyan ng auto ics wala pa rin. try ko na rin wicd parang kulang kc dalawa ang eth ng pc so ang ginawa ko lang is uninstall ang network manager ng ubuntu 9.04 at manually configure sa interfaces yung data ng eth  at ics with iptable

---

### Post by exkludge on 2009-10-04
> **killer_d76 said:**
> exkludge, ganito yung set-up ko bossing..

The Sun Cellular USB modem is plugged in at one of the USB port on my Ubuntu Laptop, on the ethernet port I have plugged in an ethernet cord (Cat5) going to the WAN port of the TP Link Router (not on the other port with designated numbers where you usually plug-in a non-wireless computer such as Desktop)

  Sun BB USB modem > USB*Ubuntu Laptop*ethernet > TP Link
(Internet Provider)       (Server)               (Router)


on Mac OSX it has a feature called **"Internet Sharing"** wherein my Laptop become a **Server** and a **Router** **at the same time**!.. I don't need to add or connect an additional device such as the  TP Link Wireless Router to share my internet connection coming from my USB Modem, this is very handy if I wanted to share my internet connection to my friend or colleague if we wanter to go on-line at the same on any given location! astig!..

May ganito bang feature/program sa Ubuntu?.. I would still prefer to use Ubuntu rather than OSX :guitar:



SideTrack: check out my Beans! **666** hehehe :D

sensya na po ngayon lang ulit ako nakabalik dito.. anyway.

ok. napi-ping na ba ng wireless-laptop mo yung ubuntu-laptop thru the TPLINK router? kung oo, malamang yung ubuntu nalang ang kailangan iconfigure. kung hindi naman, subukan mo na sa isa sa mga LAN ports ng TPLINK router ikabit yung Cat5 na galing sa ubuntu-laptop. bale syempre dapat within the same range of IP yung ubuntu-laptop at yung wireless-laptop mo.

pag nagkikita na sa ping yung dalawang laptop mo.. saka tayo pumunta sa internet sharing. :)

---

### Post by killer_d76 on 2009-12-06
thanks for all the help guys but would you believe that my problem was solved by my 12years old son?!.. I got home from work and I was surprised when i saw my son playing Urban Terror-online on our Neo Laptop and my wife was doing her regular update on her Facebook account using our Acer Aspire One netbook... what puzzles me was both of them are running Ubuntu and both are online!.. I was thinking where they are getting their internet connection since as far I know I was not successful in having Ubuntu to share our USB modem but only on Mac?!.. I asked my wife where they are connected and she mentioned that my son "Adrie" was the one who set it up!.. I asked my son how he did it and he simply mentioned... "I clicked on the wireless icon on the top right hand corner and choose "Create New Wireless Network"!  that's it! as simple as that! here's the desktop pic on our Acer Aspire One showing it is connected on our Neo Laptop via wireless connection.. and that's how to share USB Modem internet connection on Ubuntu!

---

### Post by Script Warlock on 2009-12-07
> **killer_d76 said:**
> thanks for all the help guys but would you believe that my problem was solved by my 12years old son?!.. I got home from work and I was surprised when i saw my son playing Urban Terror-online on our Neo Laptop and my wife was doing her regular update on her Facebook account using our Acer Aspire One netbook... what puzzles me was both of them are running Ubuntu and both are online!.. I was thinking where they are getting their internet connection since as far I know I was not successful in having Ubuntu to share our USB modem but only on Mac?!.. I asked my wife where they are connected and she mentioned that my son "Adrie" was the one who set it up!.. I asked my son how he did it and he simply mentioned... "I clicked on the wireless icon on the top right hand corner and choose "Create New Wireless Network"!  that's it! as simple as that! here's the desktop pic on our Acer Aspire One showing it is connected on our Neo Laptop via wireless connection.. and that's how to share USB Modem internet connection on Ubuntu!

wew i guess your getting old now dada....:P

---

### Post by killer_d76 on 2009-12-08
sure am bro.. sure am hehehe... am 33years old now and getting older hehehe.. at least I know now that I have passed to my son the importance of using Open Source Software and he has been telling it to his friends as well, though most of the time it sounded alien to them but it never missed to amaze them every time my son show them what Ubuntu can do! :popcorn:

---

### Post by jaceleon on 2009-12-08
Alam mo kuya, wag ka na po masyado maimpress sa mga bata ngayon, iba na kasi ang way of learning nila sa atin, I mean, they can learn things faster than us nung kaedad natin sila. Kakaelibs nga e...:popcorn:

Basta ang alam ko, kids these days are a bit advance when they grew up, pag kasing-edad na nila tayo.

Ako nga e, nakikita ako as alien ng mga classmates ko sa high school everytime I speak to them regarding Ubuntu, so ayos lang, basta feel ko, isa ako sa mga enlightened people. ganun din anak mo po.:P

I believe Ubuntu under these kids will have a nice future, dont you think so?

---

### Post by nesimi on 2009-12-17
> **killer_d76 said:**
> thanks for all the help guys but would you believe that my problem was solved by my 12years old son?!.. I got home from work and I was surprised when i saw my son playing Urban Terror-online on our Neo Laptop and my wife was doing her regular update on her Facebook account using our Acer Aspire One netbook... what puzzles me was both of them are running Ubuntu and both are online!.. I was thinking where they are getting their internet connection since as far I know I was not successful in having Ubuntu to share our USB modem but only on Mac?!.. I asked my wife where they are connected and she mentioned that my son "Adrie" was the one who set it up!.. I asked my son how he did it and he simply mentioned... "I clicked on the wireless icon on the top right hand corner and choose "Create New Wireless Network"!  that's it! as simple as that! here's the desktop pic on our Acer Aspire One showing it is connected on our Neo Laptop via wireless connection.. and that's how to share USB Modem internet connection on Ubuntu!

Hi,
Is your Ubuntu 9.04 or 9.10? I am seeing that your kernel is 2.6.28.16. By the way, congratulations for both having a genius child and doing the connection. And what is your wireless device and its chipset/driver etc.
Regards,

---

### Post by killer_d76 on 2009-12-17
Thanks for the kind words!.. i'm running **9.10 (2.6.31-16-generic)** on our main laptop which act as our wireless router for our wireless connection from a USB Modem our laptop has **Broadcom 3945** wireless card in it.. i tried and tested it our Acer Aspire One running **Ubuntu 9.04 (2.26.28-16-generic)** with **Atheros AR5BXB63 wireless card** and it can also share wireless connection if I plugged in the USB modem and it worked as well without flaws!

---

