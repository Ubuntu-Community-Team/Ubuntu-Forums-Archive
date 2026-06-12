---
title: "Can't print From Windows PCs to Ubuntu shared printer"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by tkinzey on 2013-12-05
I have Ubuntu 12.04 LTS installed alongside XP SP3 on this pc.  I have the printer attached via USB shared, at least I think.  None of my other pcs can see the printer (or the Ubuntu pc at all for that matter).  I'm pretty sure the workgroup is the same.  I'm really new to Ubuntu/Linux in general, so I have no idea what all needs setup/installed/configured.  Is it a rights/security issue?  Is it a software/configuration issue?  Hope somebody can help me figure it out.  I've googled and read other questions on the forums here, but to no avail.  I've done things like installing samba?  Editing smb.conf?  etc... Of course, not sure if I did those correctly or not. ;)

Thanks in advance!
Pd0x

---

### Post by philinux on 2013-12-05
This should help you.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by tkinzey on 2013-12-05
Yeah, that was the first place I checked/read.  What would servername be?  My Ubuntu hostname?

---

### Post by tkinzey on 2013-12-05
Hmmm.  I'm getting closer I think.  Apparently I didn't add that iptables line.  So I did that, and now I can see the printer from both windows 7, and from another pc running Lubuntu.  But I can't connect.  On the Lubuntu laptop when I go to "add printer", and then click on network printer, I see the hostname of the Ubuntu pc., and click all defaults through to adding it, but then when I try the test page, it complains about not being able to locate the printer.

---

### Post by tkinzey on 2013-12-05
More info:  I went on my laptop that has win7 and lubuntu dual boot installed.  Booted into Lubuntu, and I go to localhost:631, and I get the CUPS screens.  When I go to "add printer", next to "Discovered Network Printers" is the printername@hostname (HP HP Deskjet f4492 All In One Printer), that is my printer, but I still keep getting "Unable to locate printer hostname.local"  And I can not print anything, what can I check?

---

