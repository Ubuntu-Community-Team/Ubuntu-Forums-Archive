---
title: "Connecting Sun Broadband Huawei 1550 USB modem"
date: 2009-10-31
forum: Philippine Team
---

### Post by killer_d76 on 2009-10-31
My wife's sister recently subscribed to Sun Broadband Wireless and it comes with Huawei E1150 HSDPA USB modem, because she knows that I am using Sun here and it's relatively fast!.. I am using a Huawei E160 USB HSDPA MOdem which is supported by Jaunty and Karmic where in the only thing that I have to change/edit is the APN on the Network Settings, from **minternet** to **fbband** and that's it i am connected to the Net.. but when I plugged the New Huwaei E1550 HSDPA Modem from Sun Broadband wireless on my lappies USB port pfff!..nothing happened!.. did a few search on Google and this are the codes that I used to make Huawei E1550 to work on my Ubuntu lappy!

..in terminal type..

[PHP]sudo apt-get update && sudo apt-get install udev-extras[/PHP] 

then hit enter... then type..

[PHP]echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules[/PHP]

and that's it!..

enjoy!

---

### Post by jepong on 2009-11-02
great find! i used to connect and disconnect until i get a good connection. hehehehehe

---

### Post by cucay on 2010-02-04
Hi! I'm a new ubuntu user. I tried this but it didn't work. &#57432;

---

### Post by kilosan on 2010-02-04
> **cucay said:**
> Hi! I'm a new ubuntu user. I tried this but it didn't work. &#57432;

that thread is old
if you are using ubuntu 9.04
enter this on your terminal

```
sudo apt-get update && sudo apt-get install udev-extras
```

```
echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules
```

if you are using ubuntu 9.10
it is now auto detected, you just need to configure its settings to "PAP" only in the network manager>PPP Settings. if still not working try updating to the latest patch of your ubuntu.

---

### Post by kilosan on 2010-02-05
[http://www.suncellular.com.ph/broadband_faqs.php](http://www.suncellular.com.ph/broadband_faqs.php)

has anyone tried the update for mac?
will it work on ubuntu also?

---

### Post by killer_d76 on 2010-02-05
it is automatically detected by Mac OS.. i'll try and do the updte later.

---

### Post by WINPINPH1 on 2010-03-31
> **kilosan said:**
> that thread is old
if you are using ubuntu 9.04
enter this on your terminal

```
sudo apt-get update && sudo apt-get install udev-extras
``````
echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules
```if you are using ubuntu 9.10
it is now auto detected, you just need to configure its settings to "PAP" only in the network manager>PPP Settings. if still not working try updating to the latest patch of your ubuntu.

tHIS code failed in my terminal im why is that? 9.04ubuntu os im using.

---

### Post by EIxIO on 2010-04-03
Hi guys.. i got problem connecting this sun 1550 on my karmic.. it doesnt connect whenever i configure it to fbband.. and when i tried to changed it to minternet i got connection however still i cant browse internet?

---

### Post by EIxIO on 2010-04-03
oops. sorry my fault..  i simply restart then finally it works.

---

### Post by aljoriz on 2010-04-03
Usb modem switch of paul green also works.  Might I request that the thread titled be marked as SOLVED?

---

### Post by WINPINPH1 on 2010-04-04
using karmic my usb modem works like a charm.

unlike 9.04 version it wont work.

btw i still like to learn how to make it work using 9.04.

anyone knows?;)

---

### Post by aljoriz on 2010-04-04
tyr using the usb mode switch at sourceforge.

---

### Post by prvteprts on 2010-06-01
I subscribed to Sun's 350 Lite Plan which is 45 hours / Php350 per month. The modem they gave me is the Huawei 1550 model, which works out of the box. The APN I use is minternet; fbband won't work.

Is there a way to check for the remaining hours or balance online or through a program installable on Ubuntu? 

My options now are booting into Windows (which I would like to avoid) or taking out the SIM card and inserting it to a regular cellphone and then texting BALANCE to 2225.

---

### Post by prvteprts on 2010-06-01
> **prvteprts said:**
> I subscribed to Sun's 350 Lite Plan which is 45 hours / Php350 per month. The modem they gave me is the Huawei 1550 model, which works out of the box. The APN I use is minternet; fbband won't work.

Is there a way to check for the remaining hours or balance online or through a program installable on Ubuntu? 

My options now are booting into Windows (which I would like to avoid) or taking out the SIM card and inserting it to a regular cellphone and then texting BALANCE to 2225.

I found the solution. I installed Wammu (Gammu), detected the modem, and then to check the balance, I would just text "BALANCE" to 2225.

---

### Post by blizzaga4 on 2010-06-02
Can someone give me a step by step to do this with my Huawei E1552? Coz I've been searching the net and can't still find the right solution esp the Network Manager. It's actually a Globe tattoo. Thanx in advance guys.

---

### Post by blizzaga4 on 2010-06-02
Can someone give me a step by step to do this with my Huawei E1552? Coz I've been searching the net and can't still find the right solution esp the Network Manager. It's actually a Globe tattoo. Thanx in advance guys. 

I'm running Ubuntu Studio 10.4

---

### Post by vhinz on 2010-06-03
try to install usb-modeswitch from the repository

---

### Post by aljoriz on 2010-06-04
The QUICK GUIDE is in this site

[http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/](http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/)

just select GLOBE OR SMART OR DIGITEL for your provider.

---

### Post by antoniomiguel on 2010-06-05
@blizzaga4
Did the quick guide aljoriz posted helped?

There are some difference on the installation wizard since your using 10.04 and the guide is 9.04, but basically the idea is there.

---

### Post by creek23 on 2010-06-10
> **aljoriz said:**
> The QUICK GUIDE is in this site

[http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/](http://stephencuyos.com/how-to-connect-to-smartbro-prepaid-in-ubuntu-jaunty/)

just select GLOBE OR SMART OR DIGITEL for your provider.

Would it be the same for Sun? Will still have to try this night at home.

---

### Post by aljoriz on 2010-06-11
for SUN yung papalitan mo lang yung APN to minternet ata yun.

---

### Post by creek23 on 2010-06-11
> **aljoriz said:**
> for SUN yung papalitan mo lang yung APN to minternet ata yun.

ah ok. great! Can't wait to test it out.

---

### Post by killer_d76 on 2010-06-11
I use **fbband** on my post paid Sun Broadband..

---

### Post by antoniomiguel on 2010-06-12
> **killer_d76 said:**
> I use **fbband** on my post paid Sun Broadband..

Same here!

---

### Post by creek23 on 2010-06-13
> **antoniomiguel said:**
> Same here!

Tried minternet (default) and fbband. Didn't work. :(

Ni hindi na detect yung device. Any help?

---

### Post by red egg on 2010-06-15
on either APN setting "minternet" or "fbband" try putting Network mode to "HSPA/UMTS only" and check if it works. then try also on "EDGE/GPRS only"

---

### Post by antoniomiguel on 2010-06-15
> **red egg said:**
> on either APN setting "minternet" or "fbband" try putting Network mode to "HSPA/UMTS only" and check if it works. then try also on "EDGE/GPRS only"

I'm interested on this, but don't know how to change to either HSPA or EDGE. Would appreciate if you can explain more.

---

### Post by red egg on 2010-06-15
from the menu on your modem dashboard, look for "Tools" or "Settings" button
- clik and it will show some selections, mayba a "Network" button
- if there is a "Network mode" button click
- select from a droplist "Auto" or HSPA" or "EDGE"

---

### Post by antoniomiguel on 2010-06-15
> **red egg said:**
> from the menu on your modem dashboard, look for "Tools" or "Settings" button

Modem dashboard? err..im afraid i dont know how to launch this.

---

### Post by Ravskie on 2010-06-15
> **red egg said:**
> from the menu on your modem dashboard, look for "Tools" or "Settings" button
- clik and it will show some selections, mayba a "Network" button
- if there is a "Network mode" button click
- select from a droplist "Auto" or HSPA" or "EDGE"

Sir are you able to launch the modem dash board in ubuntu ???? can i know how ?

---

### Post by creek23 on 2010-06-15
**fbband** finally did work for me.

I posted my [unforgetable misadventures on this huawei e1550 on my blog]("http://creekcodes.blogspot.com/2010/06/connecting-sun-broadband-huawei-1550.html") -- hope it could be of help to someone; especially being ready dealing with Sun employees. :(

---

### Post by antoniomiguel on 2010-06-15
Good job! and nice blog too

---

### Post by creek23 on 2010-06-15
> **antoniomiguel said:**
> Good job! and nice blog too

salamat. at salamat din sa mga tulong niyo.

---

