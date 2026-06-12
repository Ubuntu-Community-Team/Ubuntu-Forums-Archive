---
title: "Acer Aspire 1640w wifi driver hell (or Acer is depowering me)"
date: 2007-08-30
forum: Other OS Talk
---

### Post by kentl on 2007-08-30
Hi!

To cut my story [SIZE=1]short[/SIZE] **[SIZE=3]long[/SIZE]**.

I've got an Acer Aspire 1640z. It came with Windows XP pre-installed together with all the usual Acer crap which is supposed to "empower" me.

I wanted to try Fiesty on it. So I used their utility to burn an DVD image of my  HDD (or so I thought). As I knew that they have a "service partition" with drivers and stuff I wanted to make sure I could wipe my HDD blank and still be able to restore my Windows XP image. I mailed Acer support and made it absolutely crystal clear that this should work. I could wipe my whole HDD, including their special partition.

So I did. Used Fiesty for a while. Then I needed to do some Visual Studio work for school (I'm a student). So I tried to restore my imaged backup DVD. No luck! It tired to access some local Windows partition, which it could not as that was all gone.

I had a spare XP license lying around. After installing it I had no drivers for my video card and my Wifi card. Acer to the rescue? [http://support.acer-euro.com/drivers/notebook/as_1640z.html](http://support.acer-euro.com/drivers/notebook/as_1640z.html) Those drivers all worked (I updated my existing drivers), except for my Wifi card.

I've installed "WLAN 802.11 (Atheros) 4.0.0.14001.zip" and/or "WLAN 802.11 (Intel) 9.0.1.9.zip" in all possible (3) combinations. The Intel driver seems to work, except that it never sees any available networks. None. Zip. Nada. This is wrong as my friend (and previously I using the first Windows XP installation from Acer) can see around 10 of them from the same location, including my own who has its router in the same room.

What can I do? :confused: Do any of you use an Acer Aspire 1640z and could tell me something about which driver is needed?

I've contacted Acer with my complaint. Hoping they will send me a real recovery DVD. But I'm not sure they will.

---

### Post by igknighted on 2007-08-30
(1) borrow an XP cd, just make sure to use your license.

(2) if you want to keep using Ubuntu, you can run a virtual machine with XP in it.  This way you can do all the .net/VS stuff for uni, but still use a decent OS.

BTW... does anyone know if you can do .net/VS compatible work with mono and whatever it's IDE is?

---

### Post by kentl on 2007-08-30
> (2) if you want to keep using Ubuntu, you can run a virtual machine with XP in it. This way you can do all the .net/VS stuff for uni, but still use a decent OS.
At the moment I'm fine with having XP on the laptop. I use Ubuntu on my other two computers. :-)

> (1) borrow an XP cd, just make sure to use your license.
I actually have a CD and have installed the OS. What I need to get *that* installation working is a working driver for my Wifi card.

However, in the long run I want to use the thwhich I bought with the laptop. I'll see if Acer will help me on that.

The big problem is finding a working driver. The problem remans. :(

---

### Post by igknighted on 2007-08-30
> **kentl said:**
> At the moment I'm fine with having XP on the laptop. I use Ubuntu on my other two computers. :-)


I actually have a CD and have installed the OS. What I need to get *that* installation working is a working driver for my Wifi card.

However, in the long run I want to use the thwhich I bought with the laptop. I'll see if Acer will help me on that.

The big problem is finding a working driver. The problem remans. :(

Try the card/chip manufacturer.  Typically HW Vendors will just point you to the people who actually make the stuff, so I'd go right there.

---

### Post by dca on 2007-08-30
If you flip it over and remove one of the covers, depending on the age of the laptop it should either have a miniPCI card or one of the ultra-new dealies...
 
The important thing is to find out which (exactly) card is being used.  It should say on the card itself.  You are right, though, the 1640-series swicthed between the Atheros & Intel cards throughout its lifetime...  In fact all Acer Aspire-series have done the same thing I guess depending on when the manf receives the parts and how much they cost at any given time...
 
You also need to go through device manager under system in control panel and make sure there's no other exclamation points on any other components.  If the card is indeed mini-PCI but the PCI bus is missing a driver or chipset drivers missing you can install WiFi drivers all day and it still won't work...

---

### Post by Bungo Pony on 2007-08-30
I wouldn't know about Acer's custom software since I wiped it when I got mine.

I agree with everyone else - find out the REAL manufacturer of your wifi and get the drivers from their site. That's what I did for all the onboard stuff. My onboard video is made by Nvidia, the onboard sound is Realtek, and I can't remember the onboard Ethernet. Nevertheless, I burned all the drivers onto a CD for safekeeping.

---

### Post by Hussien on 2008-03-09
i ant connect to internet thru acer 1640 using ubunto is there any way

---

