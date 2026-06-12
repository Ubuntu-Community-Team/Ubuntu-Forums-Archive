---
title: "New to Ubuntu, In need of guidance"
date: 2019-06-21
forum: New to Ubuntu
---

### Post by tokin08 on 2019-06-21
Hi all, I'm in need of help if anyone is able to point me the right direction it would be most appreicated. 

My Task is to create a server running Ubuntu with the GUI desktop, that can boot PC's and Laptops for hard drive formatting software

so far i have managed to install the lastest Ububtu server version, installed the desktop with webwin, configured the dhcp using ISC DHCP server (version 4 i think) and copied the formatting software to the server desktop
   The DHCP is giving out ip address's in the range i have configured on fully working OS's but i'm not seeing them in the DHCP pool when the laptops with no OS are trying boot from PXE-E53
I have googled everything i can to help with getting the rest of the setup but as of yet no luck
I'm not very clever in using the Terminal hence the desktop version of Ubuntu


Many Thanks

---

### Post by tokin08 on 2019-06-21
Apologies i should of at least introduced myself, and said hello to everyone

Hello everyone :lolflag:

---

### Post by CatKiller on 2019-06-21
Welcome!

I can't actually help with your problem, but it could probably do with some clarification so that someone can.

What you want is to set up one system so that random other systems can PXE boot your live image to run specific software. Is that right?

And you've got most of the way there, but a pure PXE boot on the random machines isn't picking up your server to load that image, but an OS boot on those machines is. Is that right, too?

---

### Post by tokin08 on 2019-06-21
Hi 
thanks for the welcome :p
[COLOR=#b22222][/COLOR]Yes thats exactly it[COLOR=#b22222] (doh!)

[/COLOR]Thanks for helping me[COLOR=#b22222]

[/COLOR][COLOR=#b22222][/COLOR]

---

### Post by tokin08 on 2019-06-24
anyone ?

---

### Post by CatKiller on 2019-06-24
I still don't know anything about PXE or DHCP, but I did see this

> 
PXE does not come with a dedicated boot protocol. It is simply DHCP  packets extended with additional DHCP options. It&#8217;s formerly known as  the bootstrap protocol. If a PXE-enabled network card sends out an DHCP  discover package, it will add DHCP option 60, which includes the string  &#8220;PXEClient:Arch:xxxxx:UNDI:yyyzzz&#8221;. Then it waits for DHCP offers. 
 It will only respond if it gets a DHCP offer including option 60  which means: I am PXE capable and able to send out boot server and boot  file information.


which sounds like it would cause your issue. The machines just looking for DHCP get that, but the PXE ones don't because they're only interested in whatever that option 60 is.

---

