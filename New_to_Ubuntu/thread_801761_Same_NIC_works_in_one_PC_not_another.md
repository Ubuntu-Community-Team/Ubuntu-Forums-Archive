---
title: "Same NIC works in one PC not another"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Porwah on 2008-05-20
Hello,

I've had quite an ordeal getting a network connection from a pesky dual booting WinXP/Ubuntu box.  Gory details here:
[http://ubuntuforums.org/showthread.php?p=4990181](http://ubuntuforums.org/showthread.php?p=4990181)

But there's an interesting new angle that maybe someone can help with.

In an attempt to get my dual booter connected, I added a separate NIC from another machine that strictly had Ubuntu (7.10) on it.  This NIC didn't work in the dual booter either.  

I retried the addon NIC in the solo Ubuntu machine with both the 7.10 and 8.04  Live CD's.  Both got a connection on boot up.  Sweet.

So can anyone tell me why this card would work in one PC (which happens to single boot) and not in the other.  Oh, and the card does get a IP and connect on the XP side on the dual booter.  It just doesn't do that on the Ubuntu side.

---

### Post by tamoneya on 2008-05-20
is it possible that the PCI slot you used was dead.  Can you place it in a different slot on the same computer?

---

### Post by Iowan on 2008-05-20
I remember a thread that mentioned some NIC settings not being reset unless machine had full power-down between OS switches.

---

### Post by spiderbatdad on 2008-05-20
was it an IBM thinkpad...the bios is designed for a specific nic

---

### Post by Porwah on 2008-05-20
No, the PCI slot works under WinXP.  :(

---

### Post by Porwah on 2008-05-20
> **spiderbatdad said:**
> was it an IBM thinkpad...the bios is designed for a specific nic

No it's a desktop with a Gigabyte GA-7VRXP motherboard.

---

### Post by Porwah on 2008-05-20
> **Iowan said:**
> I remember a thread that mentioned some NIC settings not being reset unless machine had full power-down between OS switches.

I've tried rebooting so many times.  I've tried first thing in the morning after being beat down by this for a couple hours the prior night.  Still, no difference.


Would the driver use different settings by computer? Results from ethtool say "Link Detected" and speed of 100Mb/s.  Doesn't that mean I'm connected? 

Results of ethtool -S show "tx_timeouts: 8".  I don't know what that means, but it probably has something to do with it.

---

