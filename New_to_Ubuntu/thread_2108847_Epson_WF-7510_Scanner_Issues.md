---
title: "Epson WF-7510 Scanner Issues"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by rwyeth on 2013-01-25
Hello,
I have an Epson WF-7510 all in one connected directly to my network via ethernet.  This works great for my two windows machines.  I was hoping to be able to get printer and scanner functionality on my computer running Ubuntu 12.04 desktop.  The printing was not a problem with the drivers from Epson.  And, I did install the scanner drivers.  But, apparently they are only for a USB connected device.  So, my question is, can I somehow get Ubuntu to see my network attached scanner?
Thank you,
Robert

---

### Post by rwyeth on 2013-01-25
It is under control.  SANE came to my rescue.  I logged into my DHCP/DNS server and assigned an IP address to my printer by modifying the dnsmasq.conf file.  I then went into the epkowa.conf and epson2.conf files and added my new printer IP.  Problem solved!

---

