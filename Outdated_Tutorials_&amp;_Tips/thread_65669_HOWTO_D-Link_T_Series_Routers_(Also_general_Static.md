---
title: "HOWTO: D-Link T Series Routers (Also general Static IP)"
date: 2005-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by leezer3 on 2005-09-14
Hi guys,
After spending a long while wrestling with a D-Link DSL-504T router, I thought I'd write a quick howto on how to get these irritating little machines to work. Basically, all of the D-Link T series modem-routers share a common bug in the DNS Proxy (I'm not quite sure what, something to do with IP V4/ V6), which means that Linux is unable to resolve hostnames, and means that you need to use a static IP instead.
Anyway, here's the guide:
[list=1]
[*]First you need to setup a static IP address. To do this, first go into your router, and find out the range of addresses that the DCHP server assigns- Your static IP will need to be outside this.
[*]When you have chosen your IP, go into the networking config.
[*]Choose your network device (Probably eth0), and push properties.
[*]Check the box "This device is configured", and choose static IP from the dropdown list.
[*]Enter the IP address you have chosen in the IP field, and let the subnet remain as the default (255.255.255.0)
[*]Finally here, enter as the default gatway, the address you use to access your router.
[*]Now go to this address [http://forum.portforward.com/YaBB.cgi?board=Routers;action=display;num=1115416655](http://forum.portforward.com/YaBB.cgi?board=Routers;action=display;num=1115416655) and find your ISP in the list, and make a note of thier DNS servers. (You should be able to use any of the ones in this list if your ISP is not there)
[*]Next, open up network config, and go to the DNS config. There add the DNS servers you just found. 
[*]Congratulations- Your modem-router should now be properly configured to work with Linux.
[/list] 

Cheers

-Leezer-

---

### Post by davholla on 2007-07-02
Thanks for the how to do but somehow when I was trying to do part1.  I screwed it up.  It still works people can connect to it using Win XP but Linux it is dead as a dodo.
It is not Linux per se as it can still connect using just a normal modem.  Does anyone have any ideas on how to fix it ?
My Linux machine does not have wireless but I want to have wireless for lodgers - although they can wait.

Actually I was wrong I managed to kill wireless full stop.
This is the part I have the most problems with :-
"To do this, first go into your router, and find out the range of addresses that the DCHP server assigns-!"

---

