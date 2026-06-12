---
title: "Copy  ubuntu install from Virtualbox to laptop"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by real.africa on 2008-07-06
I run Ubuntu in Virtualbox(1.4.0) on my WinXP professional PC. I have not been able to get Virtualbox 'guest additions' to work, so my Ubuntu does not have access to my DVD or hard drives on the PC. 
I want to make a copy of this Ubuntu install, which is kept updated, so I can transfer it to my laptop which now runs 8.04, but has no internet access for updating.
How can I make a copy of the Ubuntu in Virtualbox and write it to CD/DVD to transfer to my laptop?
 
Another problem is my laptop, which has Ubuntu 8.04 (only) on it, which will not play DVD's. Although I can install Ubuntu from a 'live' CD on it.

It may be that I need to 'network' my WinXP PC with my Ubuntu 8.04 laptop to give the laptop access to my internet connection. Will the 2 O/S talk to each other OK to 'network' them? Both have ethernet can I cable connect them via a simple network switch?

---

### Post by apswartz on 2008-07-06
Maybe [this post]("http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/") will help...

[http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/](http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/)

---

### Post by real.africa on 2008-07-06
> **apswartz said:**
> Maybe [this post]("http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/") will help...

[http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/](http://sysblogd.wordpress.com/2008/04/26/how-to-move-virtualboxs-guest-hard-drives-to-another-physical-location/)

Thanks for trying to help.
I also thought along similar lines to this post, but what one gets is a VDI file which I don't see ever being any good outside Virtualbox. I need to copy the good and updated install of ubuntu 8.04 (in virtualbox) to a cd that I can use to install the updated ubuntu onto my laptop.

---

### Post by real.africa on 2008-07-07
I lost patience with it all and decided to update virtualbox to the new Sun 1.6.0 version. I lost my ubuntu 8.04, which was fully up to date with all the latest downloads, because the new version will not install over the old. Innotek version has to be uninstalled first. Then to cap it all, the Sun version still refuses to install because it thinks I still have the Innotek version, even though I have rooted it out thoroughly.
What to do? Sun are very slack at responding to requests for help.

---

### Post by bumanie on 2008-07-07
You may have to go into users and groups and make sure vboxuser has been removed.

---

### Post by real.africa on 2008-07-07
> **bumanie said:**
> You may have to go into users and groups and make sure vboxuser has been removed.

Thanks for trying to help. I'm not sure this will actually do the trick. I'm using Virtualbox, (well WAS using....)on Win XP Pro SP3 with ubuntu 8.04 running as a guest. Now I don't have Virtualbox and the user/group thing you refer to, I believe, is on Ubuntu rather than Windows?
I was never aware of any vboxuser on my machine.

---

