---
title: "Network Works - Then Stops!  Why?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Andy1973 on 2008-08-09
Hi there!

I'm completely new to ubuntu, and have just installed Ubuntu 8.04 onto my desktop computer.  I was super impressed when it started up and could already see my wi-fi network, and even more impressed when I could connect straight away to the web!

HOWEVER, about 5 mins later I got a prompt telling me that there were 97 or so updates required.  Being a conscientious type, I started downloading, but then my internet connection was lost.  I could not get it back, and figured I must have done something wrong, so reinstalled Ubuntu.

Now, exactly the same thing has happened - and this time I haven't fiddled with any settings so I can ask an expert (please!), the details are:

In top right tray, I have an icon of two computers with a red triangle.  Whereas before, that menu had the name of my wireless network and a healthy percentage bar, now it only offers me a greyed out "Wired Network" and black "Manual configuration" option.  If I select Manual Config it takes me to a Network Settings Menu, but now only has Wired Connection and Point to Point Connection Options.

Not sure if any of this is relevant, but just in case:  I connect to the network with a Netgear WG 111 USB dongle.  My Network is run off a Netgear DG 834 Router.  The router is working fine with my laptop.  The Hardware test utility reckons I have a VIA Technologies VT6102 (Rhine-II)(rev 74) network controller.

One of the stickies suggested typing sudo ppoeconf into the Terminal - it came back with much unintelligible (to me) stuff, starting with "Link encap; Ethernet..." but didn't help much.

Really confused and frustrated, after everything seemed to be going so well!  Thanks for any help out there.

Andy

---

### Post by Melk79 on 2008-08-09
It seems like the Netgear WG111 has had some troubles over the various releases.  I was able to find this [link]("http://ubuntuforums.org/showthread.php?t=51993") in the Networking forum and this [link]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111") in the Ubuntu documentation.  Scroll down to the Dapper Drake part of the Ubuntu docs link and read through it.  It appears the default drivers drop connection and you need to manual use Ndiswrapper.  Since you say you're completely new to Ubuntu, it may take a bit of work to understand the process.  You'll need to run a terminal and follow the commands they provide.  Copy paste works best (NOTE: it's ctrl+shift+v in the terminal to paste.).  Hope that helps.

---

### Post by Andy1973 on 2008-08-09
Thanks for the steer!  I'll have a go at that and see where I get to.

Just can't understand how something works -and then just disappears without a trace!

Andy

---

### Post by pi.boy.travis on 2008-08-09
Did you check out Suystem-Administration-Hardware Drivers?

I am speaking of the series of menus that should be in the upper left hand corner by default.  Any additional drivers that your hardware may need will show up in there, and you just check the box next to the ones you need.

Hope this helps, and welcome to Ubuntu!

---

### Post by Andy1973 on 2008-08-09
Hi Travis,

Yes, I checked the drivers menu.  But there are "No proprietary drivers in use on this system".  Thanks for the help though!

Am trying to work out how to download Ndiswrapper on this windows laptop and transfer it to the ubuntu machine as it is not already installed.

Nothing like getting your hands dirty, early!

Andy

---

### Post by BLTicklemonster on 2008-08-09
Networking in Ubuntu has been my biggest problem since day one. Just recently in Hardy, I thought it was all fixed. I could share freely here with no problems (I don't give a flying rat's you know what about passwording everything and the kitchen sink). But recently due to upgrades, my network is back to it's "waaah, I want a password, waaaaah".

So my network is back to stupid again, and I really don't have it in me to give another flying rat's patootied to lift a stinking finger to try to remedy it.

Don't get me wrong, I've attempted to follow the guides all along and do things right even down to having to log on to the XP machines here (now the family hates me more because they have to log on to their computers now) but nothing ever worked. One thing or another once in a while actually worked, I take it back. But every time, the network would break, and I attribute that to upgrades.

A simple gui based "everything you need to do is here" program, and the resolution that the developers will not allow upgrades that will break networking would be a step in the right direction. I mean honest to GOD, if you can open a terminal and type something, you can make a gui to allow you to enter what would be entered in the terminal, so why the fuss? And the purists can stick to doing it the old fashioned way anyway, gui or not.

[/rant over]

---

### Post by pi.boy.travis on 2008-08-09
Is there a way for you to connect the Ubuntu box to the internet via Ethernet?  I believe Ndiswrapper is in the repositories, as I needed it for 7.10.  8.04 had my wireless drivers built in!  If not, you should be able to find a .deb package somewhere. . .

---

### Post by Andy1973 on 2008-08-09
ndiswrapper installed, I think!

Have blacklisted those drivers not wanted.

Struggling on, very slowly!

A

---

### Post by Andy1973 on 2008-08-09
Melk79 and Travis,

Typing this from wireless connected ubuntu desktop!!  Have never entered a line of code before and can't believe that all that gobbledegook has actually fixed it.

Gentlemen, thank you both for your time and your assistance.

Andy

---

### Post by pi.boy.travis on 2008-08-09
Congratulations!  Do not underestimate the (literally) raw power of the Terminal!

---

### Post by Melk79 on 2008-08-10
Nice job, Andy. Glad it worked out.

---

