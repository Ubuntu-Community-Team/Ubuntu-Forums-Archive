---
title: "[BCM43xx] Can't connect to network - for NO reason!"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Mazza558 on 2008-07-22
I have my wireless driver for one of my PCs (Hardy) working fine with ndiswrapper, but I can't connect to a network - the "connecting" icon next turns green and I have to enter the wireless details in again. Yes, I've checked that it's the right access code (WPA), but I just can't connect. Attached is proof that the wireless driver is working...

Help is much appreciated.

---

### Post by Mazza558 on 2008-07-22
Any ideas?

---

### Post by Mazza558 on 2008-07-22
Anyone?

---

### Post by sotiriss on 2008-07-22
I'm having also this problem. When my network hasn't password i can connect. But when i use WPA key i can't connect. I tried to solve this for months  but i couldn't.

---

### Post by Mazza558 on 2008-07-22
> **sotiriss said:**
> I'm having also this problem. When my network hasn't password i can connect. But when i use WPA key i can't connect. I tried to solve this for months  but i couldn't.

So I guess this is a common problem?

---

### Post by RequinB4 on 2008-07-22
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Follow those steps... you already have it working so i'd just dig through that thread.  I think a couple of people there had your facet of the problem fixed.

---

### Post by germanix on 2008-07-22
I have had the same problem for months, in my case however I finally solved it today. The WPA key supplied with the software for your router will not work if in the interim you have added a password to your router to make it WLAN secure. I use the Fritzbox from AVM. In my case I found out that instead of entering the standard 16 digit code supplied with the software, I entered the password that I had set myself to block users from using my router for WLAN. I am not sure if this is also the case with your problem but hope it helps.

---

### Post by Mazza558 on 2008-07-22
> **RequinB4 said:**
> [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Follow those steps... you already have it working so i'd just dig through that thread.  I think a couple of people there had your facet of the problem fixed.

Funnily enough, I wrote some of the original info for that guide - this has really got me stumped though.

---

### Post by RequinB4 on 2008-07-22
> **Mazza558 said:**
> Funnily enough, I wrote some of the original info for that guide - this has really got me stumped though.

Yeah, I wasn't saying use that method, just that I had seen this problem on these forums before with connection to that thread - a person had the same symptom but could connect to an unsecured network.  I connect to my WPA network fine, so hopefully its just an unblacklisted module or something.

---

### Post by Mazza558 on 2008-07-23
I made a bit of progress today.

By using the manual connection and entering some of the details, then switching to roaming mode, I could connect to the network (wireless bars were there). However, there's no connection info - all the IP/network addresses are "0.0.0.0" and had no actual internet connection. When I restarted, I was back to square one, with no connection at all.

---

### Post by northern lights on 2008-07-23
Exactly which Broadcom chipset are you using?

Can you post the output of ```
sudo lshw -C network
```

---

### Post by uberlube on 2008-07-23
Why not suck it up and use WEP?

---

### Post by northern lights on 2008-07-23
> **uberlube said:**
> Why not suck it up and use WEP?
+1 - agreed, actually.

I mean, I'm aware of how much tougher WPA & WPA2 are to penetrate than WEP (and I'm sure so is uberlube), but as for my private network, I don't see why it WEP wouldn't suffice.

How sensitive is your data?

---

### Post by Mazza558 on 2008-07-23
> **northern lights said:**
> +1 - agreed, actually.

I mean, I'm aware of how much tougher WPA & WPA2 are to penetrate than WEP (and I'm sure so is uberlube), but as for my private network, I don't see why it WEP wouldn't suffice.

How sensitive is your data?

Not very. The thing is, WPA worked fine before (Gutsy) - why won't it work now?

---

### Post by northern lights on 2008-07-23
Fair enough. Please see my initial questions.

In 43xx, what is xx for you? 06, 11, 18, etc?

---

### Post by Mazza558 on 2008-07-23
The output of lshw...

It's 4306.

---

### Post by fppro on 2010-07-07
This is my very first post on the Ubuntu forums, and I'm expecting great things.........
(I've been a Fedora user and occasional Ubuntu user for years though........)

On to my message:
I have a BCM4311 on a Dell Inspiron E1405.  After trying the proprietary drivers and the b43-fwcutter tool, I have had no success getting my wireless card to connect to an encrypted network.  Both WEP and WPA do not work.  Open networks work just fine.......

Does anyone have any suggestions?

---

