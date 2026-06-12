---
title: "Printer Setup w/ Airport Extreme"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by JohnTheMacGeek on 2008-07-08
I'm having trouble setting up my printer on my Ubuntu machines. It works flawlessly on my Macs. Here's the setup:

I have a HP Deskjet 5550 plugged into an Apple Airport Extreme base station via USB. I see that Ubuntu does support the printer but I can't figure out how to set it up.

I'm also having difficulty getting connected via wifi.

---

### Post by stchman on 2008-07-08
> **JohnTheMacGeek said:**
> I'm having trouble setting up my printer on my Ubuntu machines. It works flawlessly on my Macs. Here's the setup:

I have a HP Deskjet 5550 plugged into an Apple Airport Extreme base station via USB. I see that Ubuntu does support the printer but I can't figure out how to set it up.

You need to get the IP address the print server has assigned to the printer.  Let say for example the printer has an IP address of:

192.168.1.210

Go to your web browser and type:

```
localhost:631
```

This will bring up the CUPS manager.

Add the printer and use the the following for a connection.

```
socket://192.168.1.210:9100
```

---

### Post by JohnTheMacGeek on 2008-07-08
The Airport utility on my Mac (OS-X) doesn't allow me to see the IP address of the printer. How can I obtain it?

---

### Post by phidia on 2008-07-08
The IP address should be shown in Printer Setup Utility in OS X.

---

### Post by JohnTheMacGeek on 2008-07-08
> **phidia said:**
> The IP address should be shown in Printer Setup Utility in OS X.I don't see it anywhere in the printer setup utility or the airport utility.

---

### Post by stchman on 2008-07-08
> **JohnTheMacGeek said:**
> The Airport utility on my Mac (OS-X) doesn't allow me to see the IP address of the printer. How can I obtain it?

You will probably need to log into the router itself.  As to how you do that on an Airport I do not know.  I am sure there is a section on the print server.

---

### Post by flapane on 2009-02-07
did you manage to print?

---

