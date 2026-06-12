---
title: "Wireless not working, almost set up but then it disables my wired connection..."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Dark Samurai on 2008-07-10
I have been trying to get wireless to work on my laptop (using ndiswrapper) and I finally got to the stage where ndiswrapper can list it but it has an alternative driver attached to it.  I have tried black listing it, tried "rmmod"ing it, tried removing then reinstalling it... nothing is getting rid of it.  On top of all that, when I try to get my wireless to work, my wired connection disappears.  I have tried ```
sudo ifconfig eth1 down
sudo ifconfig lo up
``` and all kinds of combinations of ups and downs.  Doing the same with "iwconfig" doesn't help either.  I also have looked at this "bug" and it does not help. ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798))  Please help!

(ps. if you need more info, just tell me ;) )

---

### Post by falcon61102 on 2008-07-11
What type of card do you have and could you post the results of
```
lshw -C Network
```

---

### Post by Dark Samurai on 2008-07-11
Ok... This is some weird stuff...
So it worked (wired internet) after I rebooted my computer, then my computer froze.  I rebooted it, and IT DIDN'T WORK.  I tried rebooting with different configurations of the cord in when booting, cord out when booting, but none worked.

To answer your questions, I have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller.


*-network
      description: Wireless interface
      product: BCM4306 802.11b/g Wireless LAN Controller
      vendor: Broadcom Corporation
      physical id: 3
      bus info: pci@0000:02:03.0
      logical name: eth1
      version: 02
      serial: 00:90:4b:b2:3a:aa
      width: 32 bits
      clock: 33MHz
      capabilities: pm bus_master cap_list ethernet physical wireless 
      configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-15-generic latancy=32 link=no modulo=bcm43xx multicast=yes wireless=IEEE 802.11b/g

On a side note, I am currently running on gutsy.  If my internet works (for some freak reason) I am considering upgrading to Hardy Heron.  Should I?

Thanks a MILLION!

---

### Post by falcon61102 on 2008-07-12
I recommend the upgrade to Hardy.  But as far as your wireless goes, here is a link to a HowTo that works well.  If you've got any questions or it doesn't work out, let me know and I'll help troubleshoot.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

When you get down to Step 2 to download you drivers you'll have to switch back to windows or whatever OS has the net and then dl them from there.  Save them to a flash disk or a shared drive that you can access in Ubuntu and install from there.  Your cd should have ndiswrapper on it in case you need to install that as well.  Like I said, any questions or errors, hit me back.

Also, sorry it took a while to get back to you, for some reason I didn't get an email saying you responded...

---

### Post by Dark Samurai on 2008-07-14
Thank you so very much!  My wireless now works.  I still have issues getting my wired connection to work, but I will try to work on that and see if I can get it!
Thanks again! :)

---

