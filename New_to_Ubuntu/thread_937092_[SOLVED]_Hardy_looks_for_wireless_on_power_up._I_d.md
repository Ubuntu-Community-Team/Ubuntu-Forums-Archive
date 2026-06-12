---
title: "[SOLVED] Hardy looks for wireless on power up. I don't have it."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by TorqueyPete on 2008-10-03
How can I stop Hardy from expecting a wireless connection at log on?  I always have to open network connections and click on 'wired connection' before I can go online.
 I've looked at system/admin/network(or)network tools, but can't work out if there's anything there that will sort it out.



 And help is thanked in advance. [IMG]http://i81.photobucket.com/albums/j226/chashugh/donut.gif[/IMG]



Pete.  :)

---

### Post by Bucky Ball on 2008-10-03
In a terminal paste:[B]

nano /etc/network/interfaces[/B]

and add a hash to the line which mentions your wireless:

**# auto wlan0**

I think that should do it, if that is the name of your wireless.

---

### Post by germanix on 2008-10-03
Right click on the networking icon (two black screens top right hand corner of the desktop) make sure that wireless and networking are both enabled.

---

### Post by TorqueyPete on 2008-10-04
I guess my thread title gave the wrong idea. :oops:  Sorry.
 Is Hardy looking for a wireless connection by default?
 I don't have wireless, so why doesn't Hardy find my cable broadband connection automatically?  :confused:

  
[IMG]http://i81.photobucket.com/albums/j226/chashugh/term-error.jpg[/IMG]

---

### Post by roger_1960 on 2008-10-04
Hi

I think Bucky Ball is right, but without using terminal:

Click on the network icon (top right usually).  Click on Manual configuration.  Click on "Unlock" and enter your (sudo) password.  Select "wireless connection" and then select properties and uncheck the "enable roaming mode" box.  Then exit and reboot.

---

### Post by louieb on 2008-10-04
> **TorqueyPete said:**
> ...I don't have wireless, so why doesn't Hardy find my cable broadband connection automatically?  :confused:

Just wondering. How are you wired to your modem? Ethernet cable? usb cable? Something else?

---

### Post by Bucky Ball on 2008-10-04
```
iface eth0 inet dhcp
```Maybe try adding that at the bottom of your /etc/network/interfaces

At the moment there is no command to look for wireless or wired. Make sure your router is serving dhcp. Go to System->Admin->Network and make sure you have 'Configuration - Automatic DHCP' happening (click on the wired connection and 'properties' to find out) and that your wireless is ticked off and your wired connection is ticked on. Untick 'Enable Roaming' if it is ticked. You can play with these setting later but for now you just want to get online. :)

ps: highly unusual that Hardy doesn't find your wired connection 'out-of-the-box'. Guess there is some reason. Could you copy and paste the result of:

```
lspci
```That will let us know what you have in the machine re: network card etc.

[quote=roger_1960]Click on the network icon (top right usually). Click on Manual configuration. Click on "Unlock" and enter your (sudo) password. Select "wireless connection" and then select properties and uncheck the "enable roaming mode" box. Then exit and reboot.[/quote]

... and try that as suggested before.

---

### Post by TorqueyPete on 2008-10-05
> **Bucky Ball said:**
> ```
iface eth0 inet dhcp
```Maybe try adding that at the bottom of your /etc/network/interfaces

At the moment there is no command to look for wireless or wired. Make sure your router is serving dhcp. Go to System->Admin->Network and make sure you have 'Configuration - Automatic DHCP' happening (click on the wired connection and 'properties' to find out) and that your wireless is ticked off and your wired connection is ticked on. Untick 'Enable Roaming' if it is ticked. You can play with these setting later but for now you just want to get online. :)

ps: highly unusual that Hardy doesn't find your wired connection 'out-of-the-box'. Guess there is some reason. Could you copy and paste the result of:

```
lspci
```That will let us know what you have in the machine re: network card etc.

... and try that as suggested before.

Solved! :popcorn:

Thanks for everyone's input. It was the Auto DHCP thingy. Once I enabled that, all was as it should be. \\:D/
 Still surprised that it wasn't selected by default.

Thanx again peeps!

Pete.

---

