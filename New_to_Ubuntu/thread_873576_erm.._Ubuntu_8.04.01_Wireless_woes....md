---
title: "erm.. Ubuntu 8.04.01 Wireless woes..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Samurei on 2008-07-29
I have only recently decided to dabble in the use of ubuntu, which was recommended to me by an IT friend. Since the fatful decision to install ubuntu 8.04.01 onto my old computer, i've had mixed feelings.

fist off, i'am not sure if this should be here, but i am a total noob when it comes to linux so i thought this was the best place to try.
I'm not really having many problems with the terminal's and what not, but my biggest trouble is with wireless and getting it to work.

Thanks to (lspci -v) i know:
Ethernetcontrolled: Atheros Comms Tnc. AR5212/AR5213 Multipool MAC/Baseband prac REV 01
Subsys: DLINK System Ink, D-Link AirPlus DWL-G520
FLAGS: busmaster, medium devsel, latency 168, IRQ19
mem at feaf0000 (32bit, prefetchable) [size=64k]

I'm running the 64bit version as the computer i have installed on is an Athlon 64 +3000, i have tried to date madwifi, ndiswrapper, the windows wireless setup thingo and what ever ubuntu uses to begin with to try and get the wireless to work.

first off it was working, but only for about -2minute intervals, then it would stop, the install and use of many of the other things just created too much havok so i have re-installed ubuntu to try again.

With a fresh install of ubuntu i get reception, and as above the transmission only seems to last for a very limited time, this is with 50%+ reception on the wireless meter in the top right network log. i'm at the end of my tether as i'm not sure if 8.04.01 is 'hardy' or whatever. i'm a bit of a user, but mostly a Dr of windows, so i'm a bit keen to learn what ubuntu has to offer me, so long as i can get the wireless to work. 

(its not hardware or the router as both work fine under windows, so the h/w is ok, just not 100% on how to setup or configure hardware in ubuntu....)

cheers to anyone thats read this through and can provide me with a few pointers and the like...

---

### Post by pedrogent on 2008-07-29
Hi Samurei.

Wireless networking seems to be a problem with quite a few people unfortunately.

One thing you may want to try is installing WICD (to use instead of the default network-manager). The latest .deb can be found [here]("https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460").

You may also want to have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=587010").

I hope this is of some use.

---

