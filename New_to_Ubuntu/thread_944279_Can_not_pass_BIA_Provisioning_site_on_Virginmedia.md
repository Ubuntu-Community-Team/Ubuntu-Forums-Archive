---
title: "Can not pass BIA Provisioning site on Virginmedia"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by iangpm on 2008-10-11
I have very recently installed Ubuntu 8.04 LTS onto an HP Compaq nx8220 laptop.  The browser is Firefox 3.0.3.  I am connected to Virgin Media broadband by wired connection through a set-top-box.  My problem is that when I start Firefox to browse the internet, almost all the time I am unable to get past the ISP s 'BIA Computer Provisioning Site' .  (The provisioning site is where you introduce your computer to their network by giving it a name).  I have filled in their form, reset the set-top-box, reset my computer and generally jumped through all the hoops they held up.

I can 'Ping' websites using the DNS (Ubuntu, Google, Virginmedia, etc.) all at 100% but not the example 82.211.81.158 that is given in 'Help' 0%.  ifconfig eth1 returns sensible results with both RX and TX counts increasing as I use 'Ping'.  Sometimes, after I have Pinged a number of times, Firefox will start and let me access sites normally.  Then after varying lengths of time all links will lead back to [www.ntl.com](www.ntl.com) – the Provisioning site.

My setup works fine with Windows XP and ie6 and ie7 on two other computers we have in the house.

What do I need to do to get the Virginmedia system to reliably recognize my computer?

---

### Post by seshomaru samma on 2008-10-11
is[ this ]("http://ubuntuforums.org/showthread.php?t=541913&page=2")thread of any help ? (especially the last post)

---

### Post by iangpm on 2008-10-11
Thanks for that.  I'm not going through a router, just a direct connection to the set-top-box.  I'll give it a try and see what happens, in case the set-top-box sees itself as a router.

The problem seems to be that although I have identified my computer to the ISP, its software doesn't recognise my computer...

---

### Post by dickmorrell on 2008-11-21
Ok until last year I headed up security for NTL/Virginmedia for their consumer retail internet division and I'll try and help. 

The first response is of course you'll go to the BIA provisioning site as it's recognising the mac address of your Ubuntu box as not being recognised.

Call the helpdesk get the MAC registered then get a router and plug it into the set top box and in the admin interface clone the MAC address you registered onto it. THEN plug it into set top box and get a DHCP using the wireless / hardwired ports on the router. Or use a SmoothWall/IPCop box if you want to be a hairy smelly geek and use outdated technology (I invented it - I can say that without flames).

Please don't plug PC's straight into the settop box it wasn't designed for that, always aggregate it behind a router.

---

