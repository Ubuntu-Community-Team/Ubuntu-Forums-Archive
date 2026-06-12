---
title: "[SOLVED] Belkin wireless g USB network adaptor"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-07-20
I have an old laptop running Xubuntu and want to get the above waireless working. I have installed the windows driver under ndiswrapper but in iwconfig it shows as eth0 not wlan0 how do I fix this ????

---

### Post by AndyCooll on 2008-07-20
Taking a step back, are you sure ndiswrapper is required?

I have had a few of these (though I haven't actually used them for a couple of years) and they simply required the Ralink drivers (RT2570) installing. Recently the drivers have been built in to the kernel itself IIRC.

:cool:

---

### Post by Frenske on 2008-07-20
Which Belkin wireless g USB network adaptor does it happen to be. If it happens to be the F5D7050 v3 check the following thread [http://ubuntuforums.org/showthread.php?t=843291](http://ubuntuforums.org/showthread.php?t=843291) and the herein mentioned threads out.

Not sure what actually the problem is, wlan0 is just a name. If you found a thread dealing with your problem where wlan0 is used just change every time wlan0 is into eth0.

You could use:
```
iwlist eth0 scan
```
to make the adapter look for networks.

---

### Post by celticbhoy on 2008-07-21
thanx for the suggestions but i managed to get it up and running i had to blacklist another driver first that was stopping it doing a wireless search

---

### Post by tigerplug on 2008-07-22
Is there any chance you could provide me with the .INF and instructions on how to /what to blacklist?

I would really appreciate it! - I just cant seem to get it working!

---

### Post by A + on 2008-07-27
I have a similar issue with a Belkin Wireless G USB F5D7050 which nearly works out of the box so I'm reluctant to go messing with ndiswrapper etc. until I've an idea what's going on with it.

8.04 sees my wireless router signal via the USB, asks for WEP key and then spends some time trying to talk [all variants] [SOLVED] Belkin wireless g USB network adaptor - Ubuntu Forumsto the router.  Does anyone know what's going on here?  I assume 8.04 has drivers for the bit of hardware and for some reason the computer can't receive an address.  Does this mean that the driver simply isn't working or a different driver is interfering with it (does 'blacklisting' switch off that other driver and allow the Belkin one to function right or what???)

---

