---
title: "PeoplePC with Ubuntu, (dial up)"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by dowell22 on 2008-11-15
hey, i use people pc. (high speed isn't an option)

and i need to use it with Ubuntu 8.04.

i already installed gnome-ppp.

all my info is in there. it just doesn't detect the modem...

can anyone help me find a driver for my modem?

if it help the modem is, "PCI Data Fax SoftModem with SmartCP (COM3)"

and it's not a USB modem.

it uses a phone cord and a phone cord only. and plugs directly into the phone jack.

---

### Post by jimmy the saint on 2008-11-15
Sounds like a winmodem to me.  Youre best bet is to get a hardmodem.  The problem is that most softmodems (aka winmodems) rely on windows to do a lot of the work.  Since you don't have windows...well you see the problem.  A hard modem does all the work in the modem.  usrobotics are apparently the best but I bought a Zoom hardware modem at OfficeDepot for 60 bucks and it worked just fine.  Most hard modems will connect via serial port.

Some softmodems can be made to work, but they are a REAL pain in the butt and it is well worth the investment to just buy a decent hard modem.  I went through this trying to set up my grandmother with dial up out in the stix.  Three days with the "solutions" for winmodems was enough for me to give up.

Caution.  There are a few serial modems that are softmodems (diamond makes one) though they are rare.

I highly recommend searching for a Zoom external 56k modem that clearly indicates unix compatibility.  They are typically half the price of usrobotics and come with the cables you need.  USrobotics are outrageously expensive and don't even come with cables.

---

### Post by dowell22 on 2008-11-15
now there's something i could ask for christmas... i'll look one up... thanks

---

### Post by nitehawk777 on 2008-11-15
I got a US Robotics off of Ebay for about $1.98 (plus a little for shipping).  I had also gotten another one off of Ebay (but it didn't work so well).
Then I got REAL lucky,...and found an external Trendnet modem at a local thrift store for $1.00!!! (it's the one I've been using for months now,..and am using right now, even as I "speak"):)

These aren't the latest and greatest,...but they work great in all things linux!!!

Edit:  I remember reading in a forum recently that "People Pc" ISP had problems working with linux,....(I'll try searching and get back on that).

---

### Post by nitehawk777 on 2008-11-15
Here's two references to "PeoplesPc" ISP that I've found so far,....

[http://ubuntuforums.org/archive/index.php/t-429230.html](http://ubuntuforums.org/archive/index.php/t-429230.html)
and:
[http://www.bleepingcomputer.com/forums/topic155501.html](http://www.bleepingcomputer.com/forums/topic155501.html)

not all dialup ISPs are "linux-friendly" 
(the one's that require proprietary software to use, aren't)

for a list of low-cost dialup ISPs try looking in:

[http://www.freedomlist.com](http://www.freedomlist.com)
(that's where I found the two little dial-up services I have).

---

### Post by Bartender on 2008-11-15
Agreed, PeoplePC is a non-starter for Linux dial-up.  I know Fry's and Copper work.  Either or both may be available in your area.

---

### Post by Idaho Dan on 2008-11-15
I got a US robotics hard modem and used PeoplePc just fine with gnomeppp until DSL was finally available here. 
That was just a month ago.

---

### Post by anewguy on 2008-11-15
For your modem, do you know the manufacturer?  Do you know the chipset?  If you do "lspci" in the command line, then find your modem, do a "lscpi -vv -d <vendor>:<device>" where vendor and device should be the id's return for your modem in the first "lspci" command.  Copy/paste the results of that back here in a reply - perhaps there is a softmodem driver for your modem for Linux (don't keep your fingers crossed though).

Dave :)

EDIT:  you may also find this link helpful:

[http://http://linmodems.org/]("http://http://linmodems.org/")

---

### Post by oilchangeguy on 2008-11-15
> **jimmy the saint said:**
> Sounds like a winmodem to me.  Youre best bet is to get a hardmodem.  The problem is that most softmodems (aka winmodems) rely on windows to do a lot of the work.  Since you don't have windows...well you see the problem.  A hard modem does all the work in the modem.  usrobotics are apparently the best but I bought a Zoom hardware modem at OfficeDepot for 60 bucks and it worked just fine.  Most hard modems will connect via serial port.

Some softmodems can be made to work, but they are a REAL pain in the butt and it is well worth the investment to just buy a decent hard modem.  I went through this trying to set up my grandmother with dial up out in the stix.  Three days with the "solutions" for winmodems was enough for me to give up.

Caution.  There are a few serial modems that are softmodems (diamond makes one) though they are rare.

I highly recommend searching for a Zoom external 56k modem that clearly indicates unix compatibility.  They are typically half the price of usrobotics and come with the cables you need.  USrobotics are outrageously expensive and don't even come with cables.

your description of soft and hard modems is not correct. soft modems require software to work, not windows. hard modems are seen by the computer as hardware, and will usually work right out of the box with no problems. the problem with soft modems is, many of the companies that make them do not make their source code available to the open source world. making it very hard to write code for open source drivers.

---

### Post by Keen101 on 2008-11-16
the only internal modem I've ever got to work with ubuntu was made by 3com. 

Other than that a serial (com) modem or even a parallel port is probably your only other option.

---

### Post by jimmy the saint on 2008-11-16
> **oilchangeguy said:**
> your description of soft and hard modems is not correct. soft modems require software to work, not windows. hard modems are seen by the computer as hardware, and will usually work right out of the box with no problems. the problem with soft modems is, many of the companies that make them do not make their source code available to the open source world. making it very hard to write code for open source drivers.

I guess I did use the terms winmodems and softmodems interchangeably.  Even so, the general point that hardmodems are by far less hassle than any form of softmodem is sound, in my humble opinion.

---

