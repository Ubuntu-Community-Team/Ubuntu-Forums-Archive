---
title: "connection to internet ubuntu 12.10"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by joe_evanss on 2013-08-31
hi
have a cox internet connection on an ibm computer windows xp prof and working.
tried to unplug the working computer and plug in another with ubuntu 12.10 installed.
at one point got message connecting at 1000 mps or something to that effect but bringing
up firefox browser got message disconnected.
so, do I need another cox modem to connect or is it possible to plug into the one on the computer running windows xp prof?
any help greatly appreciated.

thanks
joe

---

### Post by sandyd on 2013-08-31
> **joe_evanss said:**
> hi
have a cox internet connection on an ibm computer windows xp prof and working.
tried to unplug the working computer and plug in another with ubuntu 12.10 installed.
at one point got message connecting at 1000 mps or something to that effect but bringing
up firefox browser got message disconnected.
so, do I need another cox modem to connect or is it possible to plug into the one on the computer running windows xp prof?
any help greatly appreciated.

thanks
joe
Hi, is this DSL or Cable?

---

### Post by grahammechanical on 2013-08-31
Stop and think for a moment.

The IBM computer has inside it the connection settings that it will use to connect the computer through the modem and onto the ISP.

Does the second computer (the one with Ubuntu) have those settings? You most certainly can use the existing modem but you need to set up a connection in Ubuntu. It would help if you told how the Ubuntu machine is connected to the modem. By wireless or by ethernet cable.

Regards.

---

### Post by joe_evanss on 2013-08-31
hi
thanks for reply, connection is by ethernet cable.
tried to enter the ip, mask,and other info from the ibm computer without success.
this is with a fairly recent asus motherboard.

thanks
joe

---

### Post by alzie on 2013-08-31
Are you planning to run both computers through the same modem or is this just a one time thing?

If you are planning on using more that 1 on a regular basis then I'd suggest getting a router and running through that.  If you don't have an issue with cables on the floor, a wired router is cheaper (and easier in my opinion) but it's not hard to set up a wireless router as well.

Modem---Router---XP
                      ---Ubuntu

The one nice thing about wifi (besides no wires) is being able to use your internet on your smart phone's wifi.

If this is a one time thing, you probably need your user name and password to access the internet through your isp.

---

### Post by TVTrukChik on 2013-09-01
Try power cycling your modem.  It's probably holding the MAC address of the first computer in its memory, so won't assign your IP address to the second one.  I said that badly.  But try rebooting the modem.

---

### Post by Iowan on 2013-09-01
Power cycling the modem might get it to recognize the second computer, but be aware that you'll (probably) need to do that each time you connect a different machine to the modem. If you plan to connect more than one computer, consider the router suggestion.

---

