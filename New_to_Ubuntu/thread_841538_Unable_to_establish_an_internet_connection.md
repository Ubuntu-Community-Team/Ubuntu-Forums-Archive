---
title: "Unable to establish an internet connection"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by RichieV on 2008-06-26
I need help with a wired Verizon Fios connection.  I've tried switching from DHCP to static and I've played with a bunch of little settings but I'm honestly not sure what I'm doing with this stuff.  

When I type in 192.168.1.1 on this computer (Windows XP) and view the list of connected devices, it does not show that computer. If I type 192.168.1.1 on the xubuntu machine I get a page load error. 

I'm using Xubuntu 8.04 and have an Actiontec MI424-WR router provided by Verizon.  I'm new to Ubuntu and am not sure what to do to troubleshoot this.  Any Ideas?

Thank you for reading.

---

### Post by Papenco on 2008-06-26
Tried rebooting?

Are you connecting by an Ethernet cable or by an USB one?

---

### Post by RichieV on 2008-06-26
Ethernet cable.  And yes I've rebooted.  I've been messing around with this for a few weeks now and have never had an internet connection.

---

### Post by cariboo on 2008-06-26
How are you trying to access your router, you don't mention anything about it. Use firefox, and in the address bar, type: [http://192,168,1,1](http://192,168,1,1) and t he admin interface should come up.

If you are having trouble connecting make sure you have roaming mode enabled in System==>Administration--Network. Click unlock, enter your password and then click the properties button, make sure that the box in the top left corner is ticked. Click OK and then Close.

Jim

---

### Post by RichieV on 2008-06-26
> **cariboo907 said:**
> How are you trying to access your router, you don't mention anything about it. Use firefox, and in the address bar, type: [http://192,168,1,1](http://192,168,1,1) and t he admin interface should come up.


I'm sorry, I thought the "how" was implied.  I used Firefox to try and access the router, by typing in that address, and I get a page load error. It never makes it to the admin interface.  If I use this computer to access the admin interface (Windows XP) and look at the list of devices connected, that machine does not appear.

---

### Post by RichieV on 2008-07-02
Alright, since this problem does not appear to have an easy solution, lets look at this from a different angle.  The reason why I want to do this is because I have a 400 gig pata drive in the xubuntu machine that I want to use to backup important stuff.  If I was to connect an ethernet cable from a Windows XP machine straight to a xubutntu machine (no router) would it be possible to transfer files directly using SMB?

---

### Post by bab1 on 2008-07-02
not with a regular ethernet cable.  You should have a switch in between or get a "straight thru" cable

Ethernet cables crossover the transmit and receive wire pairs

---

### Post by bab1 on 2008-07-02
Do you have any internet connection?  Are you familiar with the command line ie; the terminal?

---

### Post by HotCupOfJava on 2008-07-02
Is it safe for me to assume you have restarted the router as well? This does seem rather unusual. Xubuntu picked up my connection right away....

---

### Post by lazyart on 2008-07-02
> **bab1 said:**
> not with a regular ethernet cable.  You should have a switch in between or get a "straight thru" cable

Ethernet cables crossover the transmit and receive wire pairs

Umm, that's exactly backwards.  You would need a crossover cable to connect the machines directly, then assign them IP addresses to talk to each other.

A straight patch cord would need a switch or hub in between for the devices to see each other.

---

### Post by HotCupOfJava on 2008-07-02
I wonder if there is a problem with your ethernet card/hardware....you might try looking at it from that angle.

---

### Post by bab1 on 2008-07-02
Yes you are right.  It's been a long time since I made my own.

---

### Post by RichieV on 2008-07-04
> **HotCupOfJava said:**
> Is it safe for me to assume you have restarted the router as well? This does seem rather unusual. Xubuntu picked up my connection right away....

Yea, I've done that.  Actually I do that a lot, because this router is just wierd.  After about a month it will fail to assign an ip address to my devices that are frequently turned on and off (Xbox one and Xbox 360).  A quick restart solves this, but it is an annoyance.  I do not believe this has anything to do with the problem at hand.

> **HotCupOfJava said:**
> I wonder if there is a problem with your ethernet card/hardware....you might try looking at it from that angle.

I have thought about that and it is a possibility.  I haven't used this computer in years.  Everything else however seems fine.  No problems with the installation, reads disks fine, and just feels fine in general.  It's possible that it is solely the ethernet card.

> **bab1 said:**
> Do you have any internet connection?  Are you familiar with the command line ie; the terminal?

On that machine, no.  Every page comes up "load error" or "unable to establish connection" or something or other (can't remember right now).  And yes I know what terminal is but I'm not specifically familiar with any commands or anything.  This is my first experience with linux.

Thank you guys so much for your responses.  I hope this leads to some real progress.

---

### Post by RichieV on 2008-07-05
The third possibility of getting the things I want to backup onto that machine would be filling up my Ipod, 80 gigs at a time, and transfering it.  I've already tried this and it does work but it is extremely time consuming.  One thing I would be backing up is my music collection which are mostly mp3s and flacs.  Even though what I am doing is mostly for backing up purposes I would still like the ability to play these files.  By default Xubuntu is not able to play these formats without downloading packages from the internet.  How can I get those packages onto Xubuntu without the internet?

Was there a 8.04.1 release of Xubuntu? A google search turned up some things but there is nothing on the official Xubuntu website about it.  If there was, I guess I'll try installing that before I do anything else.

---

