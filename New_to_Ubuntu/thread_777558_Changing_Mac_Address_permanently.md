---
title: "Changing Mac Address permanently"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by tomor on 2008-05-01
Hi,

Is there any way to change mac address permanently? I tried macchanger but after I reboot the computer the mac address is switched again to the previous one. 

Help is appreciated

---

### Post by Monicker on 2008-05-01
> **tomor said:**
> Hi,

Is there any way to change mac address permanently? I tried macchanger but after I reboot the computer the mac address is switched again to the previous one. 

Help is appreciated


Set it in /etc/network/interfaces, for that particular interface.

hwaddress ether <mac address>

---

