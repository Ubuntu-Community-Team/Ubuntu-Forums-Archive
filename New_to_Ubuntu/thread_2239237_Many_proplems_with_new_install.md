---
title: "Many proplems with new install"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by milto on 2014-08-12
Friend talked me into Ubuntu, downloaded latest 32 bit software tied it via an ISO cd, worked great in testing mode, went ahead and did an install.Now no eathernet, no wifi, and computer will not shut down.Running on Dell Latitude D520, 3 gig ram. Ubuntu version 14.0.1 LTS. Any help would be appreciated.

---

### Post by Sef on 2014-08-12
How does it run when you boot from the CD now?

---

### Post by milto on 2014-08-12
I can get on the internet via cable Ethernet if I run in testing mode.

---

### Post by grahammechanical on 2014-08-12
When we install Ubuntu the installer likes us to be connected to the internet, preferably by ethernet. Was you able to do this? It is strange that you cannot connect by ethernet now that Ubuntu is installed. We have to take your word when you say "no ethernet, no WiFi" But have you tried to make a connection to your router?

In the top panel to the right side there should be an icon for the Network Manager. If we are connected whether by ethernet or WiFi the icon will be two arrows pointing in opposite directions. If there is no connection the icon will be of an inverted cone. What do you see?

If there is a network icon click on the icon and see if you have Networking Enabled. And also WiFi Enabled. The OS provides with us information - notifications. You need to share that information with us.

Is there another OS on this machine? Is this machine a laptop? Some laptops need the Wifi adapter switched on by a combination of key presses before Ubuntu is loaded. Also if networking is switched off in Windows then it will not work in Ubuntu.

You can also open the terminal (search for it in the Dash) and run this command.

```
rfkill list
```

This is what I see on my machine.

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


That tells me that my WiFi adapter is switched on and not switched off either by software or by some hardware switch. What do you see?

Regards.

---

### Post by milto on 2014-08-13
Way to many problems trying to install, back to Windows everything works, no trying this or that!!

---

