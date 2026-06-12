---
title: "Does Hardy Support Wireless on Dell Inspiron 1525?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Aurora@FleetBuzz on 2008-04-28
Last March, I tried to get my Dell 1525's wireless up and running in Gutsy.  After much travail, and despite the best efforts of some very helpful people here, I couldn't get it to work.  Here's that thread:
[http://ubuntuforums.org/showthread.php?t=718668](http://ubuntuforums.org/showthread.php?t=718668)

My computer has is a 32 bit machine, with Dell Wireless 1505 Wireless-N Mini-card.  I have found that corresponds to a Broadcom BCM4328 (rev 03)Chipset PCI ID 14e4:4328.  One member was kind enough to send me a link to this thread, but the thought of two more days of futility is somewhat daunting.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf)

I am thinking of giving Hardy a try, but I would like to know if it now includes the drivers for this wireless card?  I've already tried the Live CD for Hardy, but there was no response from my wireless card.  Can anyone advise if the drivers have been included in the latest release or if they have got this chipset working?  And if you got it working, are there any WPA issues?

---

### Post by keylime on 2008-04-28
Did you try the wireless from a Live CD first? I would think that should help matters.

---

### Post by Aurora@FleetBuzz on 2008-04-28
**keylime**, yes, I did.  Trouble is that Ubuntu did not recognize my wireless card or my LAN from the Live CD.  This is why I'm asking whether the drivers are included with Hardy.

---

### Post by mapes12 on 2008-04-28
I upgraded from 7.10 to 8.04 but didn't find any further support for wifi cards. In either case if you keep up to date with Update Manager in 7.10 you will get the updated kernel upgrades as they are released it the ubuntu project. These should contain further wifi driver support.

Wireless support in Linux is notoriously poor due to the lack of vendor drivers for Linux. I have a Thinkpad T23 which came with an Linksys PCMCIA wifi adaptor not supported in Linux. I used the ndiswrapper utility and configured it with the XP driver but the thing kept loosing the commection. It was driving me mad. Then I found this site:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

and bought the Comtrend PCMCIA wifi card for £10. I just plugeed it in and hey presty it worked faultlessly, everytime. 

Good luck!

---

### Post by Aurora@FleetBuzz on 2008-04-28
That sounds too easy, **mapes12**!  Does your PCMCIA conflict with the installed wireless in any way?  I will be dual booting vista along with Hardy, but if Ubuntu doesn't recognize the installed wireless card in the first place...hmmm.

---

### Post by mapes12 on 2008-04-28
In Ubuntu you will have two wireless devices: wlan0 and wlan1. Just configure the one with the native Linux driver i.e. the PCMCIA card. Likewise, Windoze will configure two wifi connections. You can configure either one you want or to remove one of them just disable it in Control Panel / System / Device Manager.

---

### Post by Aurora@FleetBuzz on 2008-04-28
> **mapes12 said:**
> In Ubuntu you will have two wireless devices: wlan0 and wlan1. Just configure the one with the native Linux driver i.e. the PCMCIA card. Likewise, Windoze will configure two wifi connections. You can configure either one you want or to remove one of them just disable it in Control Panel / System / Device Manager.

Thanks!  This is not the solution I was looking for, but it is one that will work!  Since I need to keep Vista, and don't want to have to remove the PCMCIA card from the slot each time, I'll just disable the Ubuntu-dedicated card in Vista.  So I can do this via the Control Panel?  It isn't an issue in Ubuntu as I noted earlier, Ubuntu doesn't even recognize that my wireless device is there!  

Again, sounds like a great work-around.

You linked a source for Linux compatible PCMCIA cards in the UK.  Any recommendations for US based shoppers?  My Dell Inspiron uses Express Cards, not PC.

---

### Post by sam_delta on 2008-04-28
broadcom should work under hardy if you activate hardware drivers under system > administration > hardware drivers.

if you find no drivers under hardware drivers, reinstall b43-fwcutter (broadcom drivers in hardy) using aptitude instead of synaptic

```
 sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter 
```
 
restart pc
 
and then go into system>adinistrator hardware drivers again, and see if they now appear

some threads about broadcom
[http://ubuntuforums.org/showthread.php?t=767143](http://ubuntuforums.org/showthread.php?t=767143)
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)
[http://ubuntuforums.org/showthread.php?t=762248](http://ubuntuforums.org/showthread.php?t=762248)

sam

---

### Post by Aurora@FleetBuzz on 2008-04-28
> **sam_delta said:**
> broadcom should work under hardy if you activate hardware drivers under system > administration > hardware drivers.

if you find no drivers under hardware drivers, reinstall b43-fwcutter (broadcom drivers in hardy) using aptitude instead of synaptic

sam

Thanks, sam_delta.  Is this a recent development with Hardy?  I couldn't get any restricted drivers to show up in Gutsy.  These drivers will work with ***all*** Broadcom chipsets?  Do you know of any issues with WPA?

---

### Post by sam_delta on 2008-04-28
yeah, hardy now includes new b43 drivers instead of the old bcm43xx drivers used for broadcom wireless in the past. so, you may give it a shot before buying the new card, if it dont work, then go ahaed with buying a dedicated card.

---

