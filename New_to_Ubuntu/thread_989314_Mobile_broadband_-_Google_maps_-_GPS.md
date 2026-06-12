---
title: "Mobile broadband - Google maps - GPS"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Hospadar on 2008-11-21
I'm looking into building a fantastic car PC for myself, among playing music, mayhaps videos, etc, the big thing I need it to be able to do is GPS navigation.  


I have a couple categories of questions:

-----GPS------
I've looked into this long and hard and I know there are some open-source navigation softwares that actually run in linux, but none of them have the kind of up-to-date quality maps you might find in a commercial (i.e. garmin) gps unit.  Also it's important for me to be able to look up business/restaurants/etc by name.

This leaves me with few options:

1) Run garmin's mobile PC navigation software in a VM (I gather it doesn't use the GPS properly in WINE).  This would be alright, it's good software and does what I want. - this doesn't use an internet connection.  I'm unfamiliar with VMs, would I need to do anything special to allow the VM to see the gps reciever (USB probably)

2) Google maps: is it possible to feed google maps my gps (like on an iphone, windoze mobile device, etc) so that it can put my current location on the map and update my position accordingly?
This of course would require an internet connection, which brings me to category 2


------Mobile Broadband-------
I've never had any sort of mobile broadband.  I'm wondering how easy/difficult is it to get this working under ubuntu.  Which recievers work well?  I'll probably be using ATT.
What might I expect to pay monthly for a data plan for something like this?



Thanks for all the help,
- L-tron

---

### Post by cek on 2008-11-21
Mobile broadband can be expensive -- currently I use it for internet (Verizon @ $60/month for 5GB down).

A good portion of mobile broadband cards are compatible with linux.  8.10 was INCREDIBLY easy to setup my Novatel USB727 card.  Just plug it in and network manager immediately recognizes it and allows it to connect.

---

### Post by Vegan on 2008-11-21
Expensive, you're too polite, its a rip off.

:guitar:

---

### Post by lenooh on 2009-07-05
> **Hospadar said:**
> 
This leaves me with few options:

1) Run garmin's mobile PC navigation software in a VM (I gather it doesn't use the GPS properly in WINE).  This would be alright, it's good software and does what I want. - this doesn't use an internet connection.  I'm unfamiliar with VMs, would I need to do anything special to allow the VM to see the gps reciever (USB probably)


I use garmin mobile pc with wine and ubuntu. GPS works, but you have to install the update. I followed this guide to make it work:
[http://www.mp3car.com/vbulletin/linux/128951-garmin-mobilepc-being-tested-so-far-so-good.html](http://www.mp3car.com/vbulletin/linux/128951-garmin-mobilepc-being-tested-so-far-so-good.html)

:guitar:

---

