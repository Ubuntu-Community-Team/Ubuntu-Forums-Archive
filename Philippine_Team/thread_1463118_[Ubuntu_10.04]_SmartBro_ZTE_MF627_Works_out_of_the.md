---
title: "[Ubuntu 10.04] SmartBro ZTE MF627 Works out of the box!"
date: 2010-04-26
forum: Philippine Team
---

### Post by inqui.08 on 2010-04-26
Just sharing for those nde p natry gmitin ung Smartbro USB broadband s Lucid Lynx 10.04, it works now out of the box..

Nice! Buti n lng supported n xa ngaun compared s 9.10.. It saves me lot of time especially mejo newbie p..

Ubuntu rocks! =p

:guitar:

---

### Post by aljoriz on 2010-04-26
That's great to know, I am looking forward for May1 to download ubuntu

---

### Post by leipogs23 on 2010-04-28
eto ba yung prepaid?

---

### Post by aljoriz on 2010-04-28
yup just edit the appropriate

 settings APN: Smartbro then on the PPP settings the only allowed configuration should be PAP

---

### Post by aljoriz on 2010-04-30
Sadly Huawei e1553 doesn't work with ubuntu netbook.  Just found that now, will test the desktop later to see if it is still the same

---

### Post by .Ix on 2010-05-03
Those settings were exactly what I was looking for, aljoriz! Thanks! :)

---

### Post by leipogs23 on 2010-05-03
kaya pala ayaw gumana.. me kelngan pa pala setting.hehehe

---

### Post by leipogs23 on 2010-05-06
Tinry ko sa bahay. I flugged in the smart bro..
Tapos dun sa popup...
Sinelect ko Philippines
Then smart
Then specify....smartbro
Tapos dun sa PPP
PAP nga lang chinekan ko.
Ayaw pa din...
Pano dun sa Encryption? Alin dun dapat nakacheck at alin ang indi?

---

### Post by aljoriz on 2010-05-06
> **leipogs23 said:**
> Tinry ko sa bahay. I flugged in the smart bro..
Tapos dun sa popup...
Sinelect ko Philippines
Then smart
Then specify....smartbro
Tapos dun sa PPP
PAP nga lang chinekan ko.
Ayaw pa din...
Pano dun sa Encryption? Alin dun dapat nakacheck at alin ang indi?

Yung APN at PAP lng ang gagalawin mo yung lang.

If the modem of your smartbro is Huawei E1552 white color

Do the following:
goto System>Admin>Synaptic
Search for the following
usb-modeswitch
usb-modeswitch-data

mark each and apply.

Plug your smartbro

---

### Post by lod2 on 2010-06-10
thanks for this useful info. for newbies looking for a detailed step by step, here's the link:

[http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627)

---

### Post by ginopunsalan on 2010-06-11
Does anyone know if the Smart Bro ZTE MF-637 works with Ubuntu 10.04? Thats 637 not 627.

---

### Post by Arnold Martin on 2010-07-21
> **lod2 said:**
> thanks for this useful info. for newbies looking for a detailed step by step, here's the link:
 
[http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627)
 
I want to know if you got connected, what is the color of the blinking LED?, is it blue, if it's blue, it's bad because you are in GPRS mode, it should/must be green so you can download from the net speedily.

---

### Post by kstella on 2010-07-21
> **Arnold Martin said:**
> I want to know if you got connected, what is the color of the blinking LED?, is it blue, if it's blue, it's bad because you are in GPRS mode, it should/must be green so you can download from the net speedily.

Depende yata sa model ng modem. The booklet for the Smartbro Longcheer WM66A (yung pinakabago, na hindi naman gumagana sa Ubuntu, huhuhu) says that blue means it's UMTS.

---

### Post by volaer on 2010-08-14
It does not work out of the box. You need to install usb-modeswitch. But don't worry, doing it is very simply. Here's a detailed instruction:
[http://bloggervince.blogspot.com/2010/08/how-to-activate-smartbro-in-ubuntu.html](http://bloggervince.blogspot.com/2010/08/how-to-activate-smartbro-in-ubuntu.html)

---

### Post by daxumaming on 2010-08-15
I love my MF627. also using it with Wammu to send/receive SMS. I actually prefer it over my cellphone because i hate unwanted calls.

---

### Post by tech-hero on 2010-12-06
Hi guys, im new to ubuntu. i've managed to make my Sun Wireless Broadband MF627 work for my 10.04. though sun's fair usage policy sucks, it's still a lot much better than nothing. 
 
I have a question, do you guys have an idea how to lock my MF627's data connection to UMTS? i really find it very annoying when my data connection switches from UMTS to GPRS though i really think i have UMTS signal on my room. When i'm using my Windows 7, i can set the settings to use "UMTS only" through the built in software in MF627 (the connection speed is noticeably fast and the LED indicator is BLUE). any idea how can do the same with UBUNTU?

---

### Post by alnxyz on 2011-11-22
How 'bout po ung "flashed" na mf627? Paano po un paganahin?

---

### Post by tech-hero on 2011-11-22
I guess you should do the same thing.

---

### Post by jhune_arao on 2011-11-23
> **tech-hero said:**
> do you guys have an idea how to lock my MF627's data connection to UMTS? i really find it very annoying when my data connection switches from UMTS to GPRS though i really think i have UMTS signal on my room. When i'm using my Windows 7, i can set the settings to use "UMTS only" through the built in software in MF627 (the connection speed is noticeably fast and the LED indicator is BLUE). any idea how can do the same with UBUNTU?

search mo yong....Network Connection> Tab(Mobile Broadband)>click edit> Tab(Mobile Broadband)>Advance>Type:select UMTS or GPRS.
:guitar:

---

### Post by tech-hero on 2011-11-23
> **jhune_arao said:**
> search mo yong....Network Connection> Tab(Mobile Broadband)>click edit> Tab(Mobile Broadband)>Advance>Type:select UMTS or GPRS.
:guitar:
^anong release ng UBUNTU yan sir? Wala namang ganyan sa 10.04 :D

---

### Post by jhune_arao on 2011-11-24
@tech-hero,..Ubuntu 11.10 kasi gamit ko.Unity na kasi ang menu search lang yong application tapus saka mo sya mahanap...hehehe\
kaya di ko maturo yong path ng application..:D

---

### Post by tech-hero on 2011-11-24
> **jhune_arao said:**
> @tech-hero,..Ubuntu 11.10 kasi gamit ko.Unity na kasi ang menu search lang yong application tapus saka mo sya mahanap...hehehe\
kaya di ko maturo yong path ng application..:D
haha. I mean, alam ko yung Network manager. problema, sa 10.04, walang way para malaman dun mismo sa network manager para makita yung UMTS or GPRS option. kaya kailangan pa ng terminal which is mahirap depende sa modem na gamit.

---

### Post by madc|SPYnX on 2013-01-05
> **daxumaming said:**
> I love my MF627. also using it with Wammu to send/receive SMS. I actually prefer it over my cellphone because i hate unwanted calls.


boss paturo naman kung pano nyo napagana ung mf627 ninyo.. step by step po please

---

