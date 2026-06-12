---
title: "How to connect to INTERNET"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by som88 on 2008-11-22
I installed Ubuntu on my college's pc. We have a campus wide network of **"Cisco"** which means we have got an internet connection from the ISP which is always on. The connection works absolutely fine with Windows XP but I could not find a way to connect my Ubuntu to the network with the IP adress settings. Please help.

---

### Post by lykwydchykyn on 2008-11-22
Are you able to share how you connect with Windows XP?  Is this wireless?  Wired?  Some kind of special client software required?

---

### Post by som88 on 2008-11-22
Its a wired connection

---

### Post by som88 on 2008-11-22
wait i m posting the whole config in XP

---

### Post by som88 on 2008-11-22
IP Address:172.16.12.xx
Subnet Mask:255.255.255.0
Default Gateway:172.16.12.254


Preferred DNS server:218.248.240.79
Alternate DNS server:218.248.240.135

---

### Post by lykwydchykyn on 2008-11-22
So is it a wired connection?
Did you enter all these values into Ubuntu?

Is your network manager icon displaying a network card, or showing a connection?

---

### Post by som88 on 2008-11-22
we just use the above settings in LAN to connect

---

### Post by lykwydchykyn on 2008-11-22
I'm not clear on this: DID you in fact find where to enter these settings in Ubuntu?  Or is the problem that you have entered them and it isn't working?

---

### Post by som88 on 2008-11-22
i could not find fields to enter all the values in Ubuntu

---

### Post by som88 on 2008-11-22
i cud find only three fields

---

### Post by jimmy the saint on 2008-11-22
check out this guide and see if it helps
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

### Post by som88 on 2008-11-22
> **jimmy the saint said:**
> check out this guide and see if it helps
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

thanx for the link...will let u know on monday whether it works.

---

### Post by som88 on 2009-10-11
thnx buddy it worked

---

### Post by richaoj on 2009-10-11
Right Click the network manager applet (by default upper right hand corner of the screen), then click edit connections.  Select Auto Eth0, then edit.  Go over to IPV4 settings, Select Static from the drop down, and you should be able to enter all of the information.

---

