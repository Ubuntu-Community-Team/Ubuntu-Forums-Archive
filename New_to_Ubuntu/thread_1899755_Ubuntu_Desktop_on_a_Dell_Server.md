---
title: "Ubuntu Desktop on a Dell Server??"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by rollin77 on 2011-12-24
I need to replace an old PC I was using in a home lab and I can get a Dell Poweredge 2850 for a lot less than building a new PC, (plus it would be fun to tinker with).  I don't want to use Ubuntu Server though, is it possible to install Ubuntu Desktop 10.04 version on a server like this? 

I'm not sure if anybody here has done this, they seem to be pretty cheap on e-bay though.

---

### Post by Lars Noodén on 2011-12-24
Does it have a graphics card or do you have to add one?  Real servers do not usually have graphics.  That would be the only limitation I can think of.   They often are quit noise with the fans running.

---

### Post by collisionystm on 2011-12-24
> **rollin77 said:**
> I need to replace an old PC I was using in a home lab and I can get a Dell Poweredge 2850 for a lot less than building a new PC, (plus it would be fun to tinker with).  I don't want to use Ubuntu Server though, is it possible to install Ubuntu Desktop 10.04 version on a server like this? 

I'm not sure if anybody here has done this, they seem to be pretty cheap on e-bay though.


Get your server from xbyte.com
I always buy from there and the prices are GREAT.

You can use Ubuntu-Desktop but INSTALL THE SERVER KERNEL!

I have tried that method and ubuntu-desktop as it sits will slllooowwwwww down to a crawl.

---

### Post by rollin77 on 2011-12-24
> **collisionystm said:**
> You can use Ubuntu-Desktop but INSTALL THE SERVER KERNEL!

I have tried that method and ubuntu-desktop as it sits will slllooowwwwww down to a crawl.

Is that with the server kernel installed?  I have a PDU switch that can remotely power on and off my devices, so it wouldn't be on all the time, only when I need to use it.  However, if it slows down when using it that would be a problem!

It has a 16MB ATI Radeon 7000-M video card by the way.

---

### Post by collisionystm on 2011-12-24
> **rollin77 said:**
> Is that with the server kernel installed?  I have a PDU switch that can remotely power on and off my devices, so it wouldn't be on all the time, only when I need to use it.  However, if it slows down when using it that would be a problem!

It has a 16MB ATI Radeon 7000-M video card by the way.

Here is what I would do...

install 10.04 LTS Server

Then install lxde for a gui

sudo apt-get install lxde 

and then reboot.

And no, I did not have the server kernel on the desktop version, I just know its possible to install. The server kernel is optimized to handle the input output for background applications.

---

### Post by rollin77 on 2011-12-24
Ok, thanks I may do that if I decide to go the server route.  I'm looking at an e-bay auction selling this for about $250 w/shipping from what looks like a reputable seller.

---

### Post by Stan% on 2011-12-24
> **rollin77 said:**
> I need to replace an old PC I was using in a home lab and I can get a Dell Poweredge 2850 for a lot less than building a new PC, (plus it would be fun to tinker with).  I don't want to use Ubuntu Server though, is it possible to install Ubuntu Desktop 10.04 version on a server like this? 

I'm not sure if anybody here has done this, they seem to be pretty cheap on e-bay though.

I`m using Desktop 10.04 on a PowerEdge SC440 right now. My server does not have a sound card.....so no sound but, all else works great.

---

### Post by rollin77 on 2012-02-06
I hate to bump an old thread but I wanted to offer an update that I went ahead and bought a used Dell 2850 and this is working perfectly!

I didn't install Ubuntu Server as recommended, but I might try that later on down the road to see if it offers better performance, but right now it works just fine with the regular Ubuntu 10.04 desktop edition, (I used the alternate CD disk because of the RAID setup).

Right now I'm at work and logged in looking at the desktop screen with TightVNC through an SSH tunnel.  The server only cost me $250 after shipping, perfectly accepts my 3 PCI-x quad nic cards, and has enough CPU power from the dual 2.8ghz processors to run GNS3, (Cisco router emulation software).

Thanks to you guys because otherwise I'd have no clue what I was doing! :)

---

### Post by collisionystm on 2012-02-06
sweet! Where did you end up getting the server from?

---

### Post by rollin77 on 2012-02-07
I bought it from e-bay, it was on sale for about $50 cheaper than its normal price so that helped too.  Still though, even $300 would have been far cheaper than building a new system from scratch.  It also came with a trial version of Windows 2008, I think 30 or 60 day trial, not sure, I'm not really using that anyway.

---

### Post by btindie on 2012-02-07
Modern servers support IPMI through the BMC which allows you to remotely control the power which does away for the need of a special PDU. It can piggy back NIC1 or have a dedicated NIC and also allows you to access the serial console remotely. Generally if you pay more you can also access the desktop remotely as well. Different manufactures call it by different names - HP = iLO, Dell = iDRAC.

---

