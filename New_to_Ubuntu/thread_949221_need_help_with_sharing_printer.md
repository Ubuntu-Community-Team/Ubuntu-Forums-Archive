---
title: "need help with sharing printer"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by lkb3 on 2008-10-15
Here's our setup:
I have hardy running on our desktop
My wife works at home, and has WinXP Pro running on her work laptop
Both computers are plugged into our DSL gateway.
The printer is plugged into a USB port on the Windows laptop.
I'm trying to set it up so that we can print from the desktop (hardy) to the printer.

Here's what I've done so far:
-Yes, the printer is set to allow sharing
-I went into Administration > Printing > New Printer > Windows Printer via SAMBA > and browsed for her computer
the name of her computer came up on the SMB browser, but when I clicked on it, nothing happened, and the OK button wasn't enabled.

What am I missing?
Thanks

---

### Post by trikster_x on 2008-10-15
system-->administration-->printing-->new printer-->windows printer via SAMBA

Find the make and model number so you can select the proper drivers.  If your exact model can't be found, usually model numbers close to it will work fine.  You may have to experiment with a few pages. 

Edit: Sorry my post is of no use to you.  Maybe you need to wait a few seconds for her computer to respond.

---

### Post by cariboo on 2008-10-16
There are two things you need to check, did you give your shared printer a name, and are both computers in the same workgroup. Ubuntu defaults to WORKGROUP and depending on which version of XP you have it could be MSHOME or WORKGROUP. To check the workgroup in XP go to Start-->Control Panel-->System--Computer Name. If the workgroup is MSHOME click the change button and chage the workgroup to WORKGROUP. You should then be able to see the printer in the printer installation applet.

Jim

---

### Post by lkb3 on 2008-10-16
> **cariboo907 said:**
> There are two things you need to check, did you give your shared printer a name, and are both computers in the same workgroup. Ubuntu defaults to WORKGROUP and depending on which version of XP you have it could be MSHOME or WORKGROUP. To check the workgroup in XP go to Start-->Control Panel-->System--Computer Name. If the workgroup is MSHOME click the change button and chage the workgroup to WORKGROUP. You should then be able to see the printer in the printer installation applet.

Jim


Thanks, unfortunately, due to her VPN etc, I can't change the name of the Workgroup - it actually isn't part of a workgroup, but rather part of a domain.  
Am I stuck?

---

