---
title: "How do I enable wi-fi?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by flipteo on 2008-08-10
Hi,

I have a thinkpad t42, and I don't know how to enable wireless internet, or even if I have the right hardware.  When I bought the computer on ebay, it said it had integrated wireless, but I don't know how to check.  When I look at System-> Admin-> Network, I see the 'wired connection' and the 'point to point' connection, but no wireless.

Can anyone help me?

---

### Post by rizitis on 2008-08-10
open the terminal and give this command 
```
lspci
```
then post here the results

---

### Post by flipteo on 2008-08-10
Hi,

Here ya go:


00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)

---

### Post by rizitis on 2008-08-10
I m sorry but it looks like that you dont have wireless controller.
if you stay login here for few minutes maybe somebody else (more expert) should help you...

---

### Post by flipteo on 2008-08-10
That would defintely suck if it didn't have the right hardware.

Does that "mobile" in the last line mean anything I wonder?

---

### Post by lisati on 2008-08-10
> **flipteo said:**
> That would defintely suck if it didn't have the right hardware.

Does that "mobile" in the last line mean anything I wonder?

I think the piece of hardware referred to is for a wired connection.
See [http://developer.intel.com/design/network/products/lan/controllers/82540ep.htm](http://developer.intel.com/design/network/products/lan/controllers/82540ep.htm)

---

### Post by rizitis on 2008-08-10
mobile is the Ethernet controller model for laptops
your pc dont have wifi...

---

### Post by flipteo on 2008-08-10
Maybe Ubuntu just didn't "find it" when I did the install??  If not, looks like I'll be returning this laptop.

---

### Post by rizitis on 2008-08-10
take a look here 
[http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/](http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/)
maybe you find something
but i think that your laptop dont support wifi

---

### Post by flipteo on 2008-08-10
Thanks for the link rizitis.  I've seen that page before, but I hesitate to implement anything from there since it hasn't been updated in like three years.

I just found an excellent looking [[COLOR="Sienna"]forum[/COLOR]]("http://forum.thinkpads.com") for thinkpads.  It's got a highly active Linux section too.  So right now I'm searching for a solution to my problem while I await activation.> 

I think the piece of hardware referred to is for a wired connection.
See [http://developer.intel.com/design/ne...rs/82540ep.htm](http://developer.intel.com/design/ne...rs/82540ep.htm)

I see.  Man, I really hope I can get this solved.  Judging by what I'm seeing on that thinkpad forum, everyone seems to be able to get wireless going on their t42.  Unless maybe I have the one wireless adapter that doesn't work or something.  I know t42's shipped with one of three adapter's, so who knows.  That would be just my luck if I have one that doesn't work.  Just like the video card I have on this laptop, the radeon 7500, which I don't think I'll ever be able to get compiz to work on.

---

### Post by tmartini on 2008-08-11
There is a switch on the front of Thinkpads (right next to where the left latch for the lid connects to the main part of the unit) that enable/disables wireless at a hardware level.  You may want to make sure that it's enabled (pushed to the right)...  

Also you can look up your model number hardware specs here:

[http://www.thinkwiki.org/wiki/Category:T42]("http://www.thinkwiki.org/wiki/Category:T42") 

Hope this helps..

---

