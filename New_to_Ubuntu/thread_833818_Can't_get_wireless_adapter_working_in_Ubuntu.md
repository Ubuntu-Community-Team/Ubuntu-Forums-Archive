---
title: "Can't get wireless adapter working in Ubuntu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by kuzimoto on 2008-06-18
I just recently bought a TRENDnet TEW-423PI wireless adapter for my PC. I installed it on windows first then booted up Ubuntu. I'm not quite sure how to search for wireless networks, my friend has a laptop with Ubuntu, and it shows all the available wireless networks, unlike mine. If anyone could help with the setup that would be great. I tried searching on Google for setup how-tos, I went to Trendnet's site and looked to see if my card was compatible with Ubuntu and it said it wasn't with Linux. but I saw elsewhere that you could just download a driver for ubuntu or use the windows driver. But I'm not sure how to do that. there weren't any directions specific to my card. As you probably can tell I'm a noob at this stuff. I will list below random information that I found on the box that I think may be important.

I use Ubuntu 7.10 if I have to I can upgrade to 8.04 I have the CD.

54Mbps Wireless G PCI Adapter

This is found on a little sticker on the box near the barcode:
TEW-423PI/A H/W:C1.1R
FCC ID: S9ZTEW423PI
IC:6337A-TEW423PU

---

### Post by tjwoosta on 2008-06-19
there have been others on this forum looking for the same drivers

from what i can tell the card does infact work with ndiswrapper


ndiswrapper is a tool that allows you to use certain windows drivers on linux


you will first need to find a copy of the correct windows driver, then you need to install ndiswrapper from synaptic

im not entirely sure on how to setup from there because i dont use ndiswrapper

this thread may help[URL="http://forums.fedoraforum.org/showthread.php?t=154804"]http://forums.fedoraforum.org
/showthread.php?t=154804[/URL]

just search google for "TEW-423PI ndiswrapper" and you should see a bunch of helpful links

---

