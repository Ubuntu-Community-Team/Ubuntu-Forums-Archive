---
title: "update and install new programs without internet on ubuntu box"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Warpedflash on 2008-09-30
I recently moved to university and recently got a second hand laptop. I decided to install ubuntu on it, the only problem being the only internet connection i have is on this windows desktop... is there any way for me to use something similar to apt-get to retreive the packages, copy them to my usb stick and then to the laptop?
i want a way to do this as easily as possible as i need to install a few things and would like to keep the system up to date...
its a pain trying to find all the packages i need and their dependancys etc and i need to get the sun-java6-jdk package up and running...
Thanks for any Help!

p.s the laptop has no CD drive only usb ports (that being how i installed ubuntu)

---

### Post by Zzl1xndd on 2008-09-30
How is the desktop hooked up? if its got a wireless card, or a second NIC then you could set up internet connection sharing.

---

### Post by Warpedflash on 2008-09-30
> **tweakedenigma said:**
> How is the desktop hooked up? if its got a wireless card, or a second NIC then you could set up internet connection sharing.


the desktop is wired to the only wall socket and registering a second MAC address will cost me £15 -.- i dont want to do that... i have no wireless card to share on or i would have done that... thanks for the suggestion though

---

### Post by Zzl1xndd on 2008-09-30
Ok so the desktop also only has 1 network card?

And if so do you know if the school is just using normal DHCP or if they have some kind of proprietary log in?

---

### Post by Warpedflash on 2008-09-30
> **tweakedenigma said:**
> Ok so the desktop also only has 1 network card?

And if so do you know if the school is just using normal DHCP or if they have some kind of proprietary log in?

yes im using the one on the motherboard.
erm... not sure... basically to get internet i had to dive my MAC address and can only get http traffic if i config firefox/ie/etc to go through their proxy...
so just plugging the lappy into the wall wont work..

---

### Post by cariboo on 2008-09-30
Just buy your self a cheap router and tell the IT department that your computer became useless because you were running windows, and your parents sent you up a replacement. :D

Most routers can clone MAC addresses, so you won't even have to lie.:)

Jim

---

### Post by Zzl1xndd on 2008-09-30
> **cariboo907 said:**
> Just buy your self a cheap router and tell the IT department that your computer became useless because you were running windows, and your parents sent you up a replacement. :D

Most routers can clone MAC addresses, so you won't even have to lie.:)

Jim

I was just gonna suggest this, if you don't need log in information just by a Cheap router clone your Mac Address and set up both machines with the proxy info.

---

### Post by Warpedflash on 2008-09-30
> **tweakedenigma said:**
> I was just gonna suggest this, if you don't need log in information just by a Cheap router clone your Mac Address and set up both machines with the proxy info.

me and my flatmates were thinking like this but it requires time and monies :S i was looking for a free solution, if only to get a couple of apps installed... i can leave updating...

---

### Post by Zzl1xndd on 2008-09-30
you can get .Debs from [http://www.getdeb.net/](http://www.getdeb.net/) they list the dependencies and they can also be downloaded as .debs. I'm not sure they will have all the apps you want.

---

### Post by cariboo on 2008-09-30
Another thing you could do, is if you can find a free network card or two you could set up your computer as a router by following this howto

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

I'm sure someone you know must have some old computer parts lying around.

Jim

---

### Post by Zzl1xndd on 2008-09-30
> **cariboo907 said:**
> Another thing you could do, is if you can find a free network card or two you could set up your computer as a router by following this howto

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

I'm sure someone you know must have some old computer parts lying around.

Jim

Agreed also cause you already have the windows box mac registered if you find a second card you can also use Windows Internet connection sharing the info on how to set it up is here


[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

### Post by Warpedflash on 2008-09-30
Thanks for teh replys guys :) i will prolly get a router/network card at some point

---

