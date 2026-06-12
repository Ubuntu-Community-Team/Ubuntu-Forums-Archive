---
title: "[SOLVED] Help me get PPTP working over DUN (tethered mobile phone)"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by getut on 2008-07-04
I previously had a Sprint PPC-6700 and now have a PPC-6800. I can dial and use the internet through either phone and [this]("http://ubuntuforums.org/showthread.php?t=315927") thread helped me do it.

On the other side... I have PPTP up and working through the NetManager applet, but I can only get it to work if I am attached to a physical LAN with internet access.

How do I combine the two pieces so that I can connect to my PPTP network while using my phone as a USB modem?

---

### Post by getut on 2008-07-29
Solved and even better than the old way on the PPC6700 with Gutsy or Feisty.

[http://www.synce.org/moin/SynceInstallation/Source](http://www.synce.org/moin/SynceInstallation/Source)

usb-rndis-lite

It works just like a usb network card now and shows up in netmanager applet so it works just fine with additional PPP stuff loaded on top such PPTP.

---

