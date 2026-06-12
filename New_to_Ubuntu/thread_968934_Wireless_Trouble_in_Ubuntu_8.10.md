---
title: "Wireless Trouble in Ubuntu 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by loki8941 on 2008-11-03
I have one of those dreaded broadcom cards on an acer aspire 5315, the driver is installed fine and works, the trouble is that I do not want to connect using dhcp but a fixed address. Whenever I change this in the network manager it starts acting weird and I get a "Default" wireless connnection with a strange hexadecimal password. The first time I defaulted to DHCP worked fine, when I inputed my own router ip and my own address is started acting weird. Any solution? I also would like another manager since the default one is quite broken.

---

### Post by loki8941 on 2008-11-03
no chance of help at all?

---

### Post by nothingspecial on 2008-11-03
> **loki8941 said:**
>  I also would like another manager since the default one is quite broken.

I like wicd

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by porchrat on 2008-11-03
I'm happy to see that 8.10 didn't solve all the wireless issues.  I was going to miss all those "can't get wireless working on Ubuntu" threads.  Was starting to feel like a part of me was missing.

At least we can all be safe in the knowledge that canonical can't stop the "moved a file to my trash folder now I can't delete it...it says permission denied" threads as that is an inherent permissions problem. :lolflag:

---

### Post by loki8941 on 2008-11-03
Oh well, I guess there's always slackware :D

---

### Post by mjwhitfield on 2008-11-03
I have a acer aspire 5315.

Fixed by following this guide: [http://ubuntuforums.org/showthread.php?t=610603](http://ubuntuforums.org/showthread.php?t=610603)

The wireless was the only thing that didn't work out of the box in 8.10.

---

### Post by loki8941 on 2008-11-03
Interesting, on my quad core desktop I wanted to stop using DHCP. The network manager did not allowed me to do this since it would revert back to it's original settings every time i rebooted the computer. So, I jumped into the network interfaces file and changed the stuff manually. Now not only that the network manager icon completly dissapeard, but also, no net connectivity. 

Folk ... shipping a linux distro with broken network stuff is no linux at all :(

---

### Post by loki8941 on 2008-11-03
> **mjwhitfield said:**
> I have a acer aspire 5315.

Fixed by following this guide: [http://ubuntuforums.org/showthread.php?t=610603](http://ubuntuforums.org/showthread.php?t=610603)

The wireless was the only thing that didn't work out of the box in 8.10.

As far as I know the American version of the Aspire 5315 uses Atheros WiFi, I got the other version (read third world country laptop) with Broadcom, you think that guide is compatible?

---

### Post by Yellow Pasque on 2008-11-03
I'm not fond of Network Manager. I'd rather configure wireless manually through /etc/network/interfaces (especially if using the same network each time).

---

### Post by loki8941 on 2008-11-03
> **Temüjin said:**
> I'm not fond of Network Manager. I'd rather configure wireless manually through /etc/network/interfaces (especially if using the same network each time).

Did that, but after reboot my network manager dissapeared completly! Although I configured the wired on the desktop.

---

