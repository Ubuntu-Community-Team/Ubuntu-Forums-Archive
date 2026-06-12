---
title: "Wireless driver backup?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Arlo012 on 2008-11-23
Well, in short, I installed wireless drivers on this Ubuntu laptop some time ago, and all I can remember about the process is how much of a pain it was to get working. I would really prefer not to troubleshoot getting them to work all over again in the case that when I upgrade this laptop to the next version I have problems getting wireless working and have to go back to 8.04. So, in short, is there a way to back up the drivers I am currently using for my wireless card? It's a PCMCIA wireless network card.


Thank you,
Arlo012

---

### Post by iponeverything on 2008-11-23
Drivers / Modules are kernel specific -- unless your using ndiswrapper.

What module is your wireless card using?

---

### Post by Arlo012 on 2008-11-23
I am not using ndiswrapper -- I couldn't get the card working with that. I apologize though, because I don't exactly understand what a module is. If you are referring to what model the card is, it is a Linksys WPC 11 version 3. I believe I got it working using the bcm43xx firmware, however I would prefer not to take the gamble if possible. If it is impossible, however, it's impossible.

---

### Post by iponeverything on 2008-11-24
I don't have any idea if its going to work out of the box. So, if you don't have a compelling reason to upgrade to 8.10 -- I would hold off until you have a reason to believe that it will be somewhat hassle free.

---

### Post by LeAstrale on 2008-11-24
All the bcm43xx cards i've tried worked pretty easy with ndiswrapper or fwcutter. But ofcourse thats a pain if you have no internet connection on ethernet while doing it.

could you do a "lspci | grep Network" from terminal ?

That should give us a clue on which card it is and how to make the process of installing it easier next time ;)

---

### Post by Arlo012 on 2008-11-24
> **LeAstrale said:**
> 
could you do a "lspci | grep Network" from terminal ?

That should give us a clue on which card it is and how to make the process of installing it easier next time ;)

The output of lspci | grep Network is:
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

