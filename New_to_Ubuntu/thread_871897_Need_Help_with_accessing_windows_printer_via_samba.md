---
title: "Need Help with accessing windows printer via samba on an XP machine"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by philinux on 2008-07-27
Running ubuntu on a pc on the network, XP is on another with the printer attached. I've enable sharing. 

New Printer then choose windows printer via samba then clicking Browse brings up a window "SMB browser". 

It does a scan which gives MSHOME but shows no printer. The ok button is greyed out.

---

### Post by cariboo on 2008-07-27
If you qre using Intrepid this is a bug #246440. If you enter the path to the printer manually it works eg:

```
smb://risky/EpsonSty
```

Where risky is the name of the XP computer, and EposnSty is the printer.


Jim

---

### Post by philinux on 2008-07-27
> **cariboo907 said:**
> If you qre using Intrepid this is a bug #246440. If you enter the path to the printer manually it works eg:

```
smb://risky/EpsonSty
```

Where risky is the name of the XP computer, and EposnSty is the printer.


Jim

I'm using Hardy

---

### Post by philinux on 2008-07-28
Tried the above still no joy.

---

### Post by halitech on 2008-07-28
can you ping between the 2 computers?

---

### Post by philinux on 2008-07-28
Not sure of address to ping.

On the xp machine which is connected to the router when I look at my network places it did briefly show the wireless laptop(running vista uurrgggh) and the ubuntu pc. Now it just shows an icon for the lan. Clicking that gives the lan properties dialog box. :confused:

---

### Post by halitech on 2008-07-28
windows - open a command prompt - ipconfig

ubuntu - open a terminal - ifconfig

---

